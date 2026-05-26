# Template: 9-Section Viral Video Deconstruction

> Canonical schema for the output of `prompts/01a-deconstruct-viral.md`.
> Fill EVERY field. If a field genuinely cannot be filled from the
> source material, write `(unknown, source unavailable)` and continue.
> Don't leave a field blank.

---

# Deconstruction: <handle or fixture name>

**Source URL:** <URL or "fixture: examples/<filename>">
**Format:** <duration>s <aspect ratio>, <platform>
**Engagement signal:** <likes / views / comments / shares, whatever's available>
**Scraped at:** <ISO timestamp>
**Source method:** <apify | agent-browser | fixture | pasted-transcript>
**Caption (verbatim, first 200 chars):**

> <caption text>

---

## 1. Hook (0-3s)

- **What's literally shown:**
  - (1-2 lines describing the visual in the first 3 seconds, what's
    in frame, what's moving, what's the first thing the eye lands on)

- **What's said / on-screen:**
  - (verbatim if known, the spoken line and/or the on-screen caption
    in the first 3s. Paraphrase if not, mark `(paraphrased)`.)

- **Hook archetype (named, pick ONE of 10):**
  - [ ] problem-aware
  - [ ] contrarian
  - [ ] curiosity-gap
  - [ ] specific-number / listicle
  - [ ] story-in-1-sentence
  - [ ] named-character-entering-frame
  - [ ] visual-mismatch
  - [ ] claim-then-prove
  - [ ] stat-drop
  - [ ] question-implying-contrarian-answer

- **Why this hook works:** 1 sentence.

## 2. Pattern interrupts

Enumerate EVERY moment the video resets the viewer's attention.

| Time | What changed | Function it serves |
|---|---|---|
| 0:00.0 | <on-screen caption appears in white sans bold> | <anchors muted viewer to the spoken claim> |
| 0:01.5 | <hard cut, framing tightens from MS to MCU> | <forces re-engagement, signals escalation> |
| 0:03.0 | <colour grade shifts warmer> | <signals narrative beat transition> |
| ... | | |

**Cuts per 10 seconds:** <integer>

## 3. Narrative arc (3-5 beats)

Each beat = one sentence describing what changes for the VIEWER'S
understanding or emotion. NOT a play-by-play of what happens on screen.

- **Beat 1:** <one sentence, viewer's internal shift>
- **Beat 2:** <one sentence>
- **Beat 3:** <one sentence>
- **(optional) Beat 4:** <one sentence>
- **(optional) Beat 5:** <one sentence>

## 4. Visual style

- **Subject framing:** <centred | off-centre | handheld | static | split-screen | typeset-only>
- **Camera energy:** <e.g. "calm static", "kinetic handheld", "FPV push-in", "flat doc style", "motion-graphic typography only">
- **Colour and light:** <2 anchor descriptors, e.g. "warm desaturated + golden side-key">
- **Cut frequency:** <cuts per 10s, match §2>
- **Style references (max 2, name only, don't copy):**
  - <e.g. "Casey Neistat handheld doc">
  - <e.g. "Greg Isenberg motion-graphic kinetic type">
- **Typography (if motion-graphic / typeset text present):**
  - Font family feel: <serif | sans | mono | display>
  - Weight: <light | regular | medium | bold | black>
  - Colour: <hex or descriptor>
  - Scale relative to frame: <small caption | mid-line | hero text>

## 5. Audio role

- **Music:** <present | absent>
  - If present: bed style <descriptor>, energy curve <flat | rising | pulses>, where it shifts <timestamps>
- **VO / talking-head:** <present | absent>
  - If present: tone <calm | punchy | conversational | deadpan | excited>
- **Diegetic sound:** <what's doing work, keystrokes, clicks, ambient, foley, breath>
- **Audio's specific job in this video:** <1 sentence>

## 6. Payoff

- **What the viewer gets at the end** that justifies the whole watch:
  <1-2 sentences>
- **The shape of the payoff:**
  - [ ] reveal
  - [ ] answer
  - [ ] contradiction
  - [ ] surprise
  - [ ] earned punchline
  - [ ] quiet exhale
  - [ ] actionable step
- **Why it's emotionally satisfying** for THIS specific audience:
  <1 sentence, name the audience>

## 7. CTA mechanism

- **Explicit CTA:** <verbatim if present, "none" if not>
- **Implicit CTA (pick ONE primary):**
  - [ ] save
  - [ ] share
  - [ ] screenshot
  - [ ] comment (and what the comment-bait is)
  - [ ] follow
  - [ ] click-bio

## 8. Why it went viral: hypothesis

2-3 sentences. Name 1-2 mechanics from this list (max):

- [ ] Identity-confirmation (viewer feels smart / in-the-know / part of a tribe)
- [ ] Status-transfer (viewer can share to look smart/funny/early)
- [ ] Curiosity-gap-resolution (video closes a gap it opened)
- [ ] Visual novelty (thumbnail or first-frame stops the scroll)
- [ ] Comment-bait (deliberate "wrong" detail or controversial line drove comments)
- [ ] Save-bait (screenshot-able single line or list drove saves)

<2-3 sentences explaining HOW the chosen mechanic(s) operate in this
specific video.>

## 9. What's NOT replicable (KEEP HONEST: list at least 2)

The parts of this video that depend on the original creator's specific
identity, audience, or moment, i.e. the parts you should NOT copy in
the rebuild.

- <e.g. Creator's existing audience pre-trust in their POV>
- <e.g. Creator's specific on-camera presence, voice cadence, face>
- <e.g. A current-events moment the post rode>
- <e.g. The exact wording of the hook, it's their voice, not yours>

---

## Rebuild handoff hints

- **Mechanic to keep:** <pulled from §1 + §8>
- **What to explicitly NOT copy:** <pulled from §9>
- **Suggested reel-skill target:** <cinematic-ai-reels | motion-graphic-reels>
  (apply the dispatcher rule from `prompts/03a-handoff-to-reel-skill.md`)

## Voice ship-gate status

- content-engine: <PASS | FAIL, list failing lines>
- humanizer: <PASS | FAIL, list failing lines>

(If FAIL, rewrite the failing fields and re-run. Do not ship until both
gates PASS.)
