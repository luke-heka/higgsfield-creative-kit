---
name: higgsfield-ad-critic
description: >
  Use when a Higgsfield video render has just landed and the user says
  "critique this", "give me feedback on this video", "what's wrong with
  this ad", "is this any good", "Gemini critique", "frame by frame
  critique", "review this UGC", "review this reel", or hands over an MP4
  path with no other context. Takes a rendered MP4, sends it to Google
  Gemini for frame-by-frame analysis across hook, pacing, visual
  artifacts, on-brand voice and CTA, then synthesises the feedback into
  a revision directive the user can paste straight back into Higgsfield
  for re-render. Pairs with every Higgsfield video sub-skill as the
  ship-gate critic.
user-invocable: true
metadata:
  tags: [higgsfield, ad-critic, gemini, video-critique, ugc, feedback-loop, revision, ship-gate]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
---

# Higgsfield Ad Critic

## What this is, in plain English

**One-liner:** Hand Claude a finished Higgsfield video and it sends the file to Google Gemini, a vision-capable AI, for a frame-by-frame critique, then hands back a checklist of exactly what to change.

**Use it when you want to:**
- Get a second opinion on a video ad you just rendered, before posting it
- Catch AI-giveaway glitches (warped faces, weird hands, flickering screens) before anyone else sees them
- Find out if your hook is actually strong, or just feels strong to you
- Decide whether a render is good enough to spend ad money behind

**Don't use it for:**
- Critiquing a still image, use `selrai-ad-image` instead
- Critiquing written ad copy on its own, use `ad-creative` or `content-engine` instead

**Roughly:**
- A few cents per critique (Gemini Files API, free tier covers most days)
- Two to five minutes per run
- A markdown file with the verdict, a fix-list, and a revised prompt you can paste straight back into Higgsfield

**Inputs you'll need:**
- The video file (MP4 from Higgsfield or CapCut, under 2GB)
- One sentence on who the ad is for and what action you want viewers to take
- Optional: which iteration this is, so the critic can compare to last time

## Starter packs

Three reference critique packs ship with this skill, each demonstrating a common failure mode in that ad format:

- [`starter-packs/ugc-product-ad/`](starter-packs/ugc-product-ad/), DTC UGC product ad critique. Common failure: weak soft hook + head morph.
- [`starter-packs/founder-talking-head/`](starter-packs/founder-talking-head/), coach founder-led video critique. Common failure: stiff scripted delivery.
- [`starter-packs/motion-graphic-explainer/`](starter-packs/motion-graphic-explainer/), SaaS motion-graphic explainer critique. Common failure: pacing too slow.

See [`../STARTER-PACKS.md`](../STARTER-PACKS.md) for the full index of 18 packs across all 6 sub-skills.

---

A second-opinion critic for Higgsfield video renders. Built on Edmund
Yong's Gemini feedback loop (`xyKxB8q7wQk`, "How I Make Marketing Ads
for My Apps SOLO"), reconciled with Selr AI house style and the
voice ship-gate (a final check that copy sounds like your brand, not AI)
convention (`content-engine` + `humanizer`).

The skill does NOT generate video. It reviews video. The output is a
structured critique plus a prompt-level revision directive ready to
paste back into Higgsfield.

---

## When to use this

Invoke right after any Higgsfield render finishes and the user wants a
sanity check before posting, before spending more credits, or before
running the spot as paid creative.

Common trigger phrases:

- "Critique this video."
- "Give me feedback on this ad."
- "What's wrong with this UGC?"
- "Review this reel."
- "Is the hook strong?"
- "Gemini, frame-by-frame this."
- "I just rendered v3, what should I fix?"
- "Show me the revision directive."

Do NOT invoke this skill for:

- Static image critique (route to `selrai-ad-image` or a direct Gemini
  vision call).
- Copy-only critique (route to `content-engine` or `ad-creative`).
- Vibe Motion / Remotion code critique (route to `higgsfield-vibe-motion`).
- Live A/B test analysis after posting (route to
  `apify-content-analytics` or the relevant ads platform skill).

---

## Inputs

| Input | Required | What it is |
|-------|----------|-----------|
| `video_path` | yes | Absolute path to the rendered MP4 (Higgsfield download, CapCut export, or any video file <2GB). |
| `intent_brief` | optional | One paragraph: who the ad is for, what action it should drive, which Higgsfield prompt was used, which iteration this is. If omitted, Claude asks one short clarifying question before running. |
| `brand` | optional | "Selr AI", "personal", or a client tag. Defaults to "Selr AI" and applies your brand voice rules. |
| `iteration` | optional | Integer. Used in the output filename and lets the critic compare against prior critiques in `~/board/_active/`. |

Validate first:

- File exists.
- Extension in `{mp4, mov, webm, m4v}`.
- Size under 2GB (Gemini Files API cap). If over, ask the user to
  re-export at 720p before continuing, never silently transcode.
- Duration under 60 minutes (Gemini context cap). If longer, ask the
  user to clip the section they want critiqued.

If `intent_brief` is missing, ask EXACTLY one question:

> "Quick one before I send this to Gemini, who is this ad for, and
> what's the single action you want the viewer to take? Two sentences
> is plenty."

Never ask multi-part questions.

---

## Workflow

Four stages. Each stage produces a named artifact so the next stage
can be re-run independently.

### Stage 1: Upload the video to Gemini

Preferred path: Gemini Files API via `curl` (no SDK lock-in, works on
any machine with the API key in Keeper).

```bash
# 1. Pull the API key from Keeper. NEVER write it to disk or echo it.
GEMINI_API_KEY="$(kp pass gemini-api-key 2>/dev/null)"
if [ -z "$GEMINI_API_KEY" ]; then
  echo "Gemini API key not found in Keeper. Run: kp add gemini-api-key" >&2
  exit 2
fi

# 2. Resumable upload: start a session.
VIDEO_PATH="/absolute/path/to/render.mp4"
MIME_TYPE="$(file --mime-type -b "$VIDEO_PATH")"
NUM_BYTES="$(stat -f%z "$VIDEO_PATH")"
DISPLAY_NAME="$(basename "$VIDEO_PATH")"

UPLOAD_URL="$(curl -sSL -D - \
  -H "x-goog-api-key: $GEMINI_API_KEY" \
  -H "X-Goog-Upload-Protocol: resumable" \
  -H "X-Goog-Upload-Command: start" \
  -H "X-Goog-Upload-Header-Content-Length: $NUM_BYTES" \
  -H "X-Goog-Upload-Header-Content-Type: $MIME_TYPE" \
  -H "Content-Type: application/json" \
  -d "{\"file\":{\"display_name\":\"$DISPLAY_NAME\"}}" \
  "https://generativelanguage.googleapis.com/upload/v1beta/files" \
  | tr -d '\r' | grep -i '^x-goog-upload-url:' | awk '{print $2}')"

# 3. Push the bytes.
FILE_JSON="$(curl -sSL \
  -H "Content-Length: $NUM_BYTES" \
  -H "X-Goog-Upload-Offset: 0" \
  -H "X-Goog-Upload-Command: upload, finalize" \
  --data-binary "@$VIDEO_PATH" \
  "$UPLOAD_URL")"

FILE_URI="$(echo "$FILE_JSON"  | jq -r '.file.uri')"
FILE_NAME="$(echo "$FILE_JSON" | jq -r '.file.name')"
```

The file URI is what every later prompt references. Save it to
`~/board/_active/.last-gemini-upload` so re-running Stage 2 with a
revised prompt is free (no re-upload).

Polling for processing readiness:

```bash
# Gemini processes video asynchronously. Poll until ACTIVE.
until [ "$(curl -sSL -H "x-goog-api-key: $GEMINI_API_KEY" \
            "https://generativelanguage.googleapis.com/v1beta/$FILE_NAME" \
            | jq -r '.state')" = "ACTIVE" ]; do
  sleep 4
done
```

Fallback path: if `gcloud` is configured for the same project, use
`gcloud ai files upload` instead. Both produce a file URI you can
reference in a generateContent call.

### Stage 2: Send the structured critique prompt

Use the template in "Field-by-field critique template" below. Send via
the Files API reference, NOT inline base64 (inline caps out around
20MB and most Higgsfield renders blow past that).

```bash
MODEL="gemini-2.5-pro"

CRITIQUE_RAW="$(curl -sSL \
  -H "x-goog-api-key: $GEMINI_API_KEY" \
  -H "Content-Type: application/json" \
  -d "$(jq -n --arg uri "$FILE_URI" --arg mime "$MIME_TYPE" --arg prompt "$CRITIQUE_PROMPT" '{
    contents: [{ parts: [
      { file_data: { mime_type: $mime, file_uri: $uri } },
      { text: $prompt }
    ]}],
    generationConfig: { temperature: 0.4, maxOutputTokens: 4096 }
  }')" \
  "https://generativelanguage.googleapis.com/v1beta/models/$MODEL:generateContent" \
  | jq -r '.candidates[0].content.parts[0].text')"
```

Temperature 0.4 keeps the critique grounded. Above 0.6 Gemini drifts
into flattery and away from frame-specific feedback.

### Stage 3: Parse into a revision directive

Gemini's raw output is 5 sections of prose. Parse it into a
prompt-level diff the user can paste straight back into Higgsfield.
The transform is deterministic, run it in Claude (no second model
call).

For each critique item Gemini surfaces, produce one of:

| Action verb | Where it lands in Higgsfield |
|-------------|------------------------------|
| `REWRITE_LINE` | Dialogue/script block in the original prompt |
| `RESHOOT_SHOT` | Camera + motion block in the original prompt |
| `RECAST_CHARACTER` | Character / Soul reference (link to `higgsfield-soul`) |
| `ADJUST_TIMING` | Per-chunk runtime in seconds |
| `ADD_BROLL` | New chunk to generate + CapCut overlay note |
| `RE_VOICE` | Higgsfield "Change Voice" button OR re-record VO |
| `STRENGTHEN_HOOK` | First-3-seconds block, re-write with `reels-hook-score` |
| `TIGHTEN_CTA` | Final 1-2 seconds block, plain action language |

Format the directive as a checklist the user can tick off in CapCut or
in the Higgsfield re-render UI.

### Stage 4: Optional re-render

If the user says "and re-render" / "do it" / "send it back" after
seeing the directive:

1. Read the original Higgsfield prompt from
   `~/board/_active/<project>/last-prompt.md` (every Higgsfield video
   skill writes this file on render).
2. Apply each `REWRITE_*` and `RESHOOT_*` action as a literal text
   replacement in the prompt.
3. Dispatch to the relevant Higgsfield sub-skill, usually
   `higgsfield-seedance` for UGC, `higgsfield-cinema` for narrative,
   `higgsfield-vibe-motion` for graphics, via the higgsfield MCP
   (Model Context Protocol, the plugin layer Claude uses to talk to
   external tools) connector.
4. Tag the new render with `iteration: N+1` so the next critique can
   compare deltas.

NEVER auto-render without confirmation. Print the revised prompt and
ask "Render this now? (yes/no)". Higgsfield credits are not free.

---

## Output format

Write a single markdown file inside a per-run project directory:

```
~/board/_active/ad-critic-YYYY-MM-DD/critique-<iteration>.md
```

The directory is created on first run for the day and reused for
subsequent iterations of the same project. Adjust the slug
(`ad-critic`) only if the user passes a project name in
`intent_brief`.

Frontmatter (required):

```yaml
---
critique_date: 2026-05-24
video_path: /absolute/path/to/render-v2.mp4
duration_seconds: 12
iteration: 2
brand: Selr AI
gemini_model: gemini-2.5-pro
gemini_file_uri: files/abc123
intent: 1-line summary of the intent_brief
verdict: SHIP | REVISE | RESHOOT
---
```

Body sections, in order:

1. **TL;DR**, 2-bullet verdict.
2. **Hook strength (0-3s)**, what landed, what to change.
3. **Pacing (0-end)**, beat-by-beat with timestamps.
4. **Visual artifacts**, frame numbers Gemini flagged (head morph,
   hand glitch, product flicker, eye drift).
5. **On-brand voice**, voice/copy critique scored against the brand's
   voice rules.
6. **CTA clarity**, does the viewer know what to do, and would they?
7. **Revision directive**, the checklist from Stage 3.
8. **Revised Higgsfield prompt**, drop-in replacement, ready to paste.

After saving, append a one-line entry to `~/board/_log.md`:

```
2026-05-24, Critiqued <video_path>, verdict: REVISE, iteration: 2
```

---

## Voice ship-gate

The Gemini critique is FACT (frame-by-frame observation). The revision
directive and the revised Higgsfield prompt are COPY (something you or
the team will see and act on). Copy must pass the Selr AI voice gate.

Run the body text of the critique file through both, IN ORDER, before
writing to disk:

```
draft critique
  → /content-engine grade
  → /humanizer pass
  → write to ~/board/_active/ad-critic-YYYY-MM-DD/critique-<iteration>.md
```

If either skill returns a hard-fail (em dash, AI cliche, outcome
guarantee, refund promise, support promise, "level up" / "10x" /
"unlock" / "game-changer"), rewrite the failing line until clean.

Do NOT silently strip a hard-fail without reporting it back. The
output should include a short "Voice gate result: clean" or "Voice
gate result: rewrote 3 lines (em dash, outcome guarantee, AI cliche)"
line at the very bottom so the user can audit.

---

## Field-by-field critique template

This is the literal prompt sent to Gemini. Keep it stable so feedback
is comparable across iterations.

```text
You are a senior creative director reviewing a short-form video ad
frame by frame. Watch the entire video. Then answer in five sections.
Be specific. Reference timestamps (e.g. "at 0:04") and frames where
useful. Do not flatter. Do not soften. Be the critic the founder
needs, not the cheerleader they want.

CONTEXT:
- Brand: {{brand}}
- Intent: {{intent_brief}}
- Iteration: {{iteration}}
- Tool used: Higgsfield (Seedance / Cinema Studio / Vibe Motion)
- Aspect: vertical 9:16 short-form, intended for Instagram Reels,
  TikTok, YouTube Shorts.

SECTION 1, HOOK STRENGTH (0 to 3 seconds)
- Does the opening frame stop a scroll? Why or why not?
- Is the first line of dialogue / first on-screen text a clear
  promise, problem, or pattern interrupt?
- Would a viewer with the sound off still get the hook?
- Score 1-5. Justify in one sentence.

SECTION 2, PACING
- Walk through the cuts in order. For each beat, give the
  approximate timestamp and one observation.
- Where does the video lag? Where does it rush?
- Is the runtime correct for the message, or should the cut be
  shorter or longer?

SECTION 3, VISUAL ARTIFACTS
- List every AI giveaway you can see: head morph, hand glitch,
  finger count, eye drift, lip-sync slip, product flicker, hair
  reshape, background warp, text shimmer, lighting jump.
- Give timestamp + duration for each artifact.
- Rank by severity: SHOW-STOPPER / NOTICEABLE / MINOR.

SECTION 4, ON-BRAND VOICE
- Is the script's tone consistent with the brand context above?
- Where does the language sound generic-AI versus specific-human?
- Flag any of these slop terms if present: game-changer, 10x,
  crushing it, killing it, secret sauce, level up, unlock,
  next-level, transform, revolutionise.
- Suggest 1-2 voice-true replacement lines.

SECTION 5, CTA CLARITY
- What is the call to action?
- Is the action specific enough that a viewer can do it without
  guessing?
- Where is it placed in the runtime, and could it land harder?
- One sentence rewrite.

FINAL VERDICT: SHIP / REVISE / RESHOOT.
ONE-SENTENCE WHY.
```

Variables in `{{double braces}}` get substituted via `sed` before send.

---

## Worked example

Input:

- `video_path`: `~/Downloads/createskills-ugc-v1.mp4`
- `intent_brief`: "UGC ad for createskills.io, solo founders, AI-curious.
  Drive sign-ups to the free skill. This is iteration 1."
- Render came out of Higgsfield Seedance 2.0, 12s, 9:16 720p.

Gemini's raw section 3:

> At 0:04 the woman's head briefly enlarges by ~20% over 14 frames
> before snapping back. SHOW-STOPPER. At 0:09 the laptop screen text
> shimmers and re-renders. NOTICEABLE. Lip-sync slips at 0:10, mouth
> closes on a vowel. NOTICEABLE.

Stage 3 transforms that into:

```
[ ] RESHOOT_SHOT 0:03-0:05, head morph. Re-prompt: lock framing
    medium-close on shoulders up, no zoom, no rapid expression
    change. Add to negative-constraints: "head enlarging, scale
    changes, face morphing".
[ ] ADD_BROLL 0:09-0:10, overlay a 1.5s product UI clip to cover
    the screen text shimmer. CapCut step, no re-render needed.
[ ] RE_VOICE 0:10, Higgsfield "Change Voice" or re-record the
    line "...curious about AI" with a cleaner mouth close.
```

Gemini's raw section 1:

> The first line is "Hey guys so I've been using this app called
> CreateSkills." Soft opener. Doesn't promise or problem. A viewer
> with no sound sees a generic talking head, no hook frame.

Stage 3 transforms:

```
[ ] STRENGTHEN_HOOK 0:00-0:03, rewrite line. Replace
    "Hey guys so I've been using this app called CreateSkills"
    with one of:
      (a) "If you're trying to ship one small skill a week, this
          is what I'm using."
      (b) "Most founders skip the boring skill. Here's the boring
          skill I built first."
      (c) "Three weeks ago I couldn't ship a Claude skill. Here's
          what changed."
    Add an on-screen text overlay of the chosen line (CapCut step)
    so the hook lands with sound off.
```

The revised Higgsfield prompt (Stage 4 draft, pre-confirmation):

```
[selfie-handheld, 9:16, 720p, 12s]
Megan, early 30s, sitting at a desk in a sunlit home office, laptop
visible to side, monitor in background, warm natural light.
LOCK FRAMING: medium-close shoulders up, NO zoom, NO scale change
across the clip.
ENERGY: warm, low-key, like she's telling a friend, not pitching.

DIALOGUE (12s total, 3 beats):
Beat 1 (0-3s, looking at camera): "Three weeks ago I couldn't ship
a Claude skill. Here's what changed."
Beat 2 (3-9s, looking down at laptop, then back to camera):
"I stopped trying to learn everything. I picked one tiny skill ,
a daily summary, and shipped it."
Beat 3 (9-12s, direct to camera): "If that's where you're stuck,
the free skill is on createskills dot io."

NEGATIVE CONSTRAINTS: head enlarging, scale changes, face morphing,
hand glitch, eye drift, text shimmer on screens.
```

Verdict written into the critique file: REVISE.

---

## Failure modes

Each one is named so the agent can fix without help.

### Gemini quota hit (429)

Symptoms: `RESOURCE_EXHAUSTED` in the JSON response.

Fix:

1. Switch the model from `gemini-2.5-pro` to `gemini-2.5-flash` for
   the next call. Flash has a separate quota bucket and is fine for
   structured critiques (the upgrade to Pro is only worth it on
   ambiguous artifacts).
2. If Flash is also rate-limited, wait 60 seconds and retry once.
3. If still failing, write a partial critique file with `verdict:
   QUOTA_RETRY` and a note for the user to re-run with
   `--model flash` later.

Never silently drop the critique. Always write the file with a
verdict, even if the verdict is "I could not finish."

### Video format unsupported

Symptoms: upload returns 400 with `Invalid argument` or processing
state stays at `FAILED`.

Fix:

1. Confirm the file's container with `ffprobe -v error -show_entries
   format=format_name "$VIDEO_PATH"`.
2. If container is `matroska,webm` or anything non-standard, ask the
   user to re-export from CapCut or Higgsfield as MP4 (H.264 + AAC).
3. Do NOT transcode silently, silent transcodes hide quality drops
   that change the critique.

### No clear feedback (Gemini returns generic praise)

Symptoms: section bodies say things like "great pacing, strong hook"
with no timestamps.

Fix:

1. Re-run Stage 2 with temperature dropped to 0.2.
2. Append this line to the template:
   "If a section has no concrete frame-level observation, write
   'NO FINDING' for that section. Never invent praise."
3. If the second pass is also generic, the critic-output is the
   problem, not the video. Flag in the output as
   `verdict: CRITIC_FAILED, manually review`.

### Video too long for context window

Symptoms: 400 response with `context length exceeded` or processing
state never reaches `ACTIVE`.

Fix:

1. Ask the user which 60-second window matters most.
2. Use `ffmpeg -ss <start> -t 60 -i in.mp4 -c copy clip.mp4` to cut.
3. Critique the clip and note in the file that the critique was on a
   sub-segment, not the full video.

### Higgsfield prompt file not found (Stage 4)

Symptoms: `~/board/_active/<project>/last-prompt.md` does not exist.

Fix:

1. Ask the user to paste the original Higgsfield prompt once.
2. Save it to the expected path before applying the revision diff.
3. Future renders from the upstream skill (`higgsfield-seedance` etc)
   should write this file automatically, if they don't, file a bug
   against the upstream sub-skill.

### Keeper unavailable / API key missing

Symptoms: `kp pass gemini-api-key` returns nothing.

Fix:

1. Ask the user once: "Gemini API key isn't in Keeper. Want me to add
   it? Paste the key and I'll store it in Keeper, then continue."
2. Store via `kp add gemini-api-key` (the wrapper handles the prompt).
3. Never write the key to `.env`, JSON, shell history, or echo it back
   to the user.

---

## Shared assets

This skill links to (does not duplicate) two shared docs in the
Higgsfield skill pack:

- `../shared/higgsfield-prompt-skeletons.md`, the canonical
  field-by-field prompt skeletons used when rewriting the Higgsfield
  prompt in Stage 4. The revised prompt MUST conform to the relevant
  skeleton (Image / Video / Carousel-Slide / Rebuild / Testimonial).
- `../shared/capcut-finishing.md`, the universal post-production
  recipe. Any `ADD_BROLL`, `ADJUST_TIMING`, or audio-fix actions in
  the revision directive should reference the matching section in
  this doc so the user knows exactly what CapCut step to take.

Both docs are loaded by every Layer-2 workflow skill (the
orchestration tier that strings together multiple Higgsfield steps)
in this pack. Read them before authoring the revision directive so
the verbs you emit map to actions the user already knows.

---

## Composition with other skills

This skill plugs into the same Layer-2 orchestration patterns the
other Higgsfield sub-skills use.

### Pattern A: Single-shot UGC critique loop

```
user uploads render
  → higgsfield-ad-critic (Stages 1-3)
  → critique file written
  → user reviews directive
  → higgsfield-ad-critic (Stage 4, on confirm)
       → higgsfield-seedance OR higgsfield-cinema (re-render)
  → loop back to Stage 1 on next iteration
```

### Pattern B: Multi-chunk UGC critique (Alex Robinson workflow)

```
user uploads stitched CapCut export
  → higgsfield-ad-critic on full stitch
  → critique flags ONE bad chunk (e.g. chunk 3, head morph at 0:04)
  → revision directive scopes the fix to chunk 3 only
  → user re-renders chunk 3 in higgsfield-seedance
  → user re-stitches in CapCut (capcut-finishing.md)
  → optional: re-critique the new stitch
```

### Pattern C: Cinema Studio narrative critique

```
user uploads narrative render
  → higgsfield-ad-critic with intent_brief = "narrative ad, 30s"
       → critique template stays the same
       → BUT temperature drops to 0.3 (narrative needs less
         interpretation)
  → revision directive lands on Cinema Studio prompt blocks
  → user re-renders via higgsfield-cinema
```

### Pattern D: Vibe Motion critique (graphics, not video)

```
user uploads Vibe Motion export
  → higgsfield-ad-critic
       → SKIP section 3 (visual artifacts), Vibe Motion is code,
         not pixel-prediction, artifacts don't apply
       → keep sections 1, 2, 4, 5
  → revision directive lands on Vibe Motion chat refinements
    (e.g. "make entrance faster", "change headline font")
```

### Pattern E: Pre-paid-ads gate

```
user has a render they want to spend money behind
  → higgsfield-ad-critic with verdict required = SHIP
  → if REVISE or RESHOOT, block the spend
  → if SHIP, hand off to the paid-ads skill (ad-creative, paid-ads)
    for headline + primary text generation
```

---

## Cost notes

- Gemini Files API: free tier covers ~1500 requests/day on Flash, much
  less on Pro. A 60s 720p video uses 1 request to upload + 1 to
  generate. Comfortable for the daily-iteration use case.
- Re-running Stage 2 against the same `FILE_URI` does NOT re-upload.
  Use this for free A/B prompt-template experiments.
- Files auto-delete from the Gemini Files API after 48h. After that
  the URI 404s and you'll need to re-upload.
- If running this skill 10+ times per day, switch the default model to
  `gemini-2.5-flash` and only escalate to Pro when Flash returns a
  generic critique (see "No clear feedback" failure mode).

---

## Verification checklist before saving the critique file

The skill runs these checks itself, not the user.

- [ ] Frontmatter present and complete.
- [ ] All five sections have at least one timestamp reference.
- [ ] Revision directive has at least one actionable item OR an
      explicit "SHIP, no changes" line.
- [ ] Voice gate result line present at the bottom.
- [ ] File written to `~/board/_active/ad-critic-YYYY-MM-DD/critique-N.md`.
- [ ] Log line appended to `~/board/_log.md`.
- [ ] If Stage 4 ran: revised prompt file written and original
      preserved at `<original>.prev`.

If any check fails, fix before reporting back. Do not surface a
half-written critique to the user.

---

## Related skills

- `higgsfield-seedance`, UGC video renders that this skill critiques
- `higgsfield-cinema`, narrative renders that this skill critiques
- `higgsfield-vibe-motion`, code-based graphics renders (sections 3
  not applicable)
- `higgsfield-recall`, silent fixes for known Higgsfield failure
  patterns, applied BEFORE the next render
- `higgsfield-troubleshoot`, operator-side problems (auth, MCP, billing)
- `reels-hook-score`, quantitative hook scoring, pairs with section 1
- `content-engine`, voice gate, MANDATORY
- `humanizer`, AI-writing scrub, MANDATORY
- `ad-creative`, generates the paid-headline variants once verdict is SHIP
- `apify-content-analytics`, post-launch performance critique (different scope)
