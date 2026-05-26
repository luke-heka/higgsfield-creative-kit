# Stage 7: Aggregated Higgsfield Prompts

Read `05-social-posts.md` and `06-influencer-army.md`. Reformat every
Higgsfield prompt from those two files into a single clean file the user
pastes straight into the Higgsfield UI.

**This is the demo paste target.** When the user is on camera running
through the Higgsfield UI, they paste from this file. Make it clean.

## File Structure

Write the output file in this exact structure:

````markdown
# Higgsfield Prompts: <Brand>, <YYYY-MM-DD>

Aggregated from Stages 5 (Social Posts) and 6 (Influencer Briefs).
Paste each block straight into the Higgsfield UI. Skill that emitted this
file: `higgsfield-cmo-agent` v1.0.0.

> **Carousel posts are NOT included**, those render via
> `carousel-generator` (Remotion + Fraunces). Higgsfield only renders
> background imagery for slide 4 / slide 7 IF requested.
>
> **Text-only posts are NOT included**, X / LinkedIn text-only posts
> don't need Higgsfield assets.
>
> Every prompt below has been voice-graded (Stage 5) and brief-aligned
> (Stage 3). Re-grade if you edit.

---

## Stage 5: Social Post Prompts

### Segment 1: Post 1, IG Reel, 9:16, 12s

```
<full Higgsfield prompt, paste-ready, fenced block with NO language tag>
```

### Segment 1: Post 2, IG Story, 9:16, 5s

```
<full Higgsfield prompt>
```

### Segment 1: Post 4, IG Reel, 9:16, 8s

```
<full Higgsfield prompt>
```

> Segment 1 Post 3 was an IG carousel, rendered via carousel-generator
> (template: 5-tips). Not included here.
> Segment 1 Post 5 was a LinkedIn text-only post, no Higgsfield prompt.

### Segment 2: Post 1, YouTube long-form thumbnail, 16:9, still

```
<full Higgsfield prompt>
```

... continue for every video / still post across all segments ...

---

## Stage 6: Influencer Reference Shots (Optional)

These are Higgsfield prompts the brand can pre-render and send to the
influencer as REFERENCE material (visual brief), NOT for the influencer
to use as their own content. They show the creator the look the brand
wants without dictating their shooting style.

Only include if the per-handle brief from Stage 6 requested a reference
shot. Most nano-tier briefs don't need this.

### @<handle> (Tier: micro, Platform: IG): Concept reference shot

```
<full Higgsfield prompt for the reference shot>
```

### @<handle> (Tier: micro, Platform: YouTube): Thumbnail composition reference

```
<full Higgsfield prompt>
```

... continue ...

---

## Paste Workflow

1. Open https://higgsfield.ai in the browser.
2. Pick the model that matches the prompt's asset type:
   - **Video prompts** (5-15s, 9:16) → Cinema Studio (Veo 3 / Kling /
     Seedance, pick by camera-energy spec in the prompt)
   - **Still prompts** (1:1, 4:5, 9:16, 16:9) → Image Generation
     (Nano Banana 2 for product-on-white, GPT Image 2.0 for UGC
     characters, Soul 2.0 for character consistency)
   - **Reference shots** → Same as stills, but mark as "reference" in
     the project workspace, don't publish
3. Paste the prompt block (everything inside the fenced code block).
4. Hit generate.
5. If output doesn't match: read the EXCLUDE field, usually a missing
   exclude is the issue.

## Notes

- Each prompt is a single code block, no commentary, no edits inside the
  fence.
- Prompts in this file are voice-graded against the Selr ban-list (for
  Selr runs) and the Stage 3 creative brief.
- If you edit a prompt manually, re-grade through `content-engine` before
  using.
- For multi-chunk videos (e.g. a 30s Reel split into 3x 10s chunks), each
  chunk gets its own entry below the parent post header.
- Element tags (`@product`, `@logo`, `@founder`) should already be set up
  in the Higgsfield Elements panel. See
  `../shared/element-tagging.md` for setup.
````

## Aggregation Rules

1. **One prompt per code block.** No commentary inside the fence.
2. **Code block fenced, NO language tag.** (Plain triple-backtick.)
3. **Header above each prompt** names the segment + post + surface +
   format so the user can find which prompt is which on the fly:
   - `### Segment N, Post M, <Surface>, <aspect>, <duration>`
4. **Skip carousel posts.** Note them as "rendered via carousel-generator"
   in a quote line above the next prompt.
5. **Skip text-only posts.** Note them as "no Higgsfield prompt" in a
   quote line.
6. **Include Stage 6 influencer reference shots ONLY** if the per-handle
   brief explicitly requested a reference shot. Most don't need this ,
   the brief tells the creator what to make, not what to copy.
7. **Multi-chunk posts get one entry per chunk** with sub-headers:
   - `### Segment N, Post M, Chunk A, <action description>`
   - `### Segment N, Post M, Chunk B, <action description>`

## NO Voice Gate at This Stage

This is a mechanical reformat. The prompts inside have already been voice-
graded in Stages 5-6. Do not re-grade, that wastes a voice-gate cycle.

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/07-higgsfield-prompts.md
```

## Post-Stage Summary (Surface to User)

After the file is saved, output:

```
Stage 7 complete.

Output: ~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/07-higgsfield-prompts.md

Total prompts: N
  - Video prompts: N
  - Still prompts: N
  - Reference shots: N (influencer optional)

Carousel posts (rendered via carousel-generator, not included here): N
Text-only posts (no Higgsfield needed): N

Paste workflow: open higgsfield.ai, pick model by asset type, paste each
fenced block, hit generate.

Full campaign output dir: ~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/

Campaign files:
  00-brief.md
  01-segments.md
  02-channel-plan.md
  03-creative-briefs.md
  04-launch-plan.md
  05-social-posts.md
  06-influencer-army.md
  07-higgsfield-prompts.md   ← THE PASTE TARGET

GHL contact tag: campaign-<brand-slug>-<date>
Notion campaign page: <URL>
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| Carousel posts have prompts in this file | Filter out, carousels go through carousel-generator |
| Text-only posts have prompts | Filter out, no visual to render |
| Headers missing format spec | Add `<aspect>, <duration>` so user knows what model to pick |
| Multi-chunk posts collapsed into one prompt | Split into Chunk A / Chunk B with action description |
| Re-graded prompts (changed inside the fence) | DON'T, the gate happened at Stage 5/6 |
| Reference shots included for every handle | Only include if brief asked for one, most nano don't need |
| Missing brand-slug in filename | Re-derive from 00-brief.md |
| Code blocks have ```text language tag | Strip, keep plain ``` |

## Demo Output Sketch (Selr AI Melbourne Workshop: abbreviated)

````markdown
# Higgsfield Prompts: Selr AI Melbourne Workshop, 2026-05-24

Aggregated from Stages 5 (Social Posts) and 6 (Influencer Briefs).
Paste each block straight into the Higgsfield UI. Skill that emitted this
file: `higgsfield-cmo-agent` v1.0.0.

> Carousel posts are NOT included, those render via carousel-generator.
> Text-only posts are NOT included.
> Every prompt below has been voice-graded (Stage 5) and brief-aligned
> (Stage 3).

---

## Stage 5: Social Post Prompts

### Segment 1: Post 1, IG Reel, 9:16, 12s

```
12 seconds 9:16, medium close-up handheld, AU operator man in his early
40s mid-install on a beat-up MacBook with terminal visible, in a Selr AI
workshop room with 11 other operators around tables in soft focus
background, mid-morning side light through tall windows natural soft,
slight handheld drift forward over the duration no zoom, 50mm equivalent
shallow depth of field background gently out of focus, palette dark wood
table cream walls Selr purple notebook accent in lower right of frame,
fine film grain natural skin texture, audio: ambient workshop room tone
with a single Slack notification ping at second 9, product visibility:
Selr purple appears once as notebook spine in lower-right third of frame
for the full 12 seconds, EXCLUDE: drone shots tripod stability stock-photo
poses AI-glossy skin gradient backgrounds overlay text watermark hashtag
overlays neon AI-circuit aesthetic.
```

### Segment 1: Post 2, IG Story still, 9:16, 1 frame

```
2K vertical 9:16, medium close-up shot, AU operator woman in her late 30s
closing her laptop with a small contented exhale, modern shared workspace
in soft focus background, late afternoon side window light warm natural,
50mm full-frame look shallow depth of field background gently out of
focus, warm muted palette cream wood-grain Selr purple lanyard accent,
fine film grain natural skin texture not plastic, product visibility:
Selr purple lanyard visible on her neck slightly out of focus, EXCLUDE:
AI-glossy skin gradient backgrounds drop shadows emoji watermark overlay
text hashtag overlays stock-photo poses fake smiles neon circuits.
```

> Segment 1 Post 3 was an IG carousel, rendered via carousel-generator
> (template: 5-tips). Not included here.

### Segment 1: Post 4, IG Reel, 9:16, 8s

```
8 seconds 9:16, medium handheld over-shoulder, an AU operator typing
into a terminal then pressing return as a Slack notification pings on
screen, in a Selr workshop room mid-day background out of focus, mid-
morning side window light natural, slight handheld static, 35mm equivalent
shallow depth of field, palette dark wood cream walls subtle Selr purple
accent on coffee cup, fine film grain natural texture, audio: keyboard
clicks then single Slack ping at second 6, product visibility: Selr
purple coffee cup edge visible in lower-left for the full 8 seconds,
EXCLUDE: tripod stability drone shots AI-glossy screen recordings stock-
poses neon circuits gradient overlays watermark.
```

> Segment 1 Post 5 was a LinkedIn text-only post, no Higgsfield prompt.

### Segment 2: Post 1, YouTube long-form thumbnail, 16:9, still

```
2K 16:9 horizontal, medium close-up shot, AU founder man in his late 30s
standing in a Melbourne coworking space looking at the camera with a slight
serious expression, holding an open MacBook with terminal visible to his
chest, mid-morning side window light natural soft, 35mm full-frame look
moderate depth of field background slightly out of focus revealing 11
seated operators behind him, palette dark wood cream walls Selr purple
accent on his lanyard, fine film grain natural skin texture not plastic,
product visibility: Selr purple lanyard visible centred on his neck,
EXCLUDE: thumbnail-style yellow circles arrow overlays drop shadows
gradient backgrounds AI-glossy skin neon circuits stock founder poses
fake smiles oversaturated colors.
```

... (continues for every video + still post across all 4 segments) ...

---

## Stage 6: Influencer Reference Shots (Optional)

### @<microcreator1> (Tier: micro, Platform: IG): Concept reference shot

```
6 seconds 9:16, medium close-up handheld selfie style, AU SMB founder
opening her laptop at 6am in a quiet home office with one lamp on, golden
hour orange sunrise just starting through window behind her, slight
handheld natural wobble no zoom, 50mm equivalent shallow depth of field
background soft, warm muted palette dawn-orange cream walls Selr purple
coffee cup accent, fine film grain natural skin texture not plastic,
audio: ambient room tone single coffee-cup placement clink at second 2,
product visibility: Selr purple coffee cup in lower-right third visible
for the full 6 seconds, EXCLUDE: studio lighting AI-glossy skin perfect
posing flowers in background gradient backgrounds drop shadows watermark.
```

---

## Paste Workflow

1. Open https://higgsfield.ai in the browser.
2. Pick the model that matches the prompt's asset type:
   - Video prompts (5-15s, 9:16) → Cinema Studio (Veo 3 / Kling / Seedance)
   - Still prompts (1:1, 4:5, 9:16, 16:9) → Image Generation (Nano Banana 2 / GPT Image 2.0 / Soul 2.0)
   - Reference shots → Image generation, marked as reference in project
3. Paste the prompt block (everything inside the fenced code block).
4. Hit generate.
5. If output doesn't match: read the EXCLUDE field, usually a missing
   exclude is the issue.

## Notes

- Each prompt is a single code block, no commentary, no edits inside the
  fence.
- Prompts in this file are voice-graded against the Selr ban-list and
  Stage 3 creative briefs.
- For multi-chunk videos, each chunk has its own entry.
- Element tags (@product, @logo, @founder) should already be set up in
  Higgsfield Elements panel.
````

## Next Step (After Stage 7)

Stage 7 is the final pipeline stage. After it saves, the campaign run is
complete. The skill outputs a final summary (see "Post-Stage Summary"
above) and stops.

Optional next actions the user can take:

- Send the first batch of DMs from the Notion page (Stage 6 output)
- Paste prompts into Higgsfield UI to start rendering (Stage 7 file)
- Hand off the launch plan to whoever owns each row (Stage 4 file)
- Run `carousel-generator` for any carousel-shaped posts (Stage 5 noted
  the template choices)
- Wire community-drop CTAs through `community-publishing-pipeline`
  (Stage 5 noted the keywords)
