# Prompt 01a, Deconstruct a Viral Video

You have a `raw-post.json` (or a fixture from `examples/`) with a viral
post's caption, hashtags, on-screen text, video poster, duration, and
engagement counts. If the user pasted a transcript, use that as
additional input.

## Your job

Produce a structured 9-section breakdown of *why this worked*, in a form
that lets the next prompt rebuild it for a different brand. Match the
schema in `templates/deconstruction.md` exactly.

## Output schema (9 sections, fill all)

```
# Deconstruction: <handle or fixture name>

**Source URL:** <URL or "fixture">
**Format:** <duration>s <aspect>, <platform>
**Engagement signal:** <likes / views / comments, whatever's available>
**Caption (verbatim):** <first 200 chars of caption>

---

## 1. Hook (0-3s)

- **What's literally shown:** (1-2 lines)
- **What's said / on-screen:** (verbatim if known, paraphrase if not)
- **The pattern (named archetype):** name ONE of the 10 hook archetypes
  from `../shared/hook-bank-100.md`:
  - problem-aware
  - contrarian
  - curiosity-gap
  - specific-number / listicle
  - story-in-1-sentence
  - named-character-entering-frame
  - visual-mismatch
  - claim-then-prove
  - stat-drop
  - question-implying-contrarian-answer
- **Why this hook works:** 1 sentence.

## 2. Pattern interrupts

Enumerate EVERY moment the video resets the viewer's attention. For
each interrupt:

| Time | What changed | Function it serves |
|---|---|---|
| 0:00.0 | (e.g. on-screen caption appears in white sans bold) | (e.g. anchors muted viewer to the spoken claim) |
| 0:01.5 | (e.g. hard cut, framing tightens from MS to MCU) | (e.g. forces re-engagement, signals escalation) |
| ... | | |

**Cuts per 10 seconds:** <number>

## 3. Narrative arc

3-5 beats. Each beat = one sentence describing what changes for the
viewer's understanding or emotion. NOT a play-by-play of what happens
on screen, describe the INTERNAL shift in the viewer.

- Beat 1: <one sentence>
- Beat 2: <one sentence>
- Beat 3: <one sentence>
- (optional) Beat 4: <one sentence>
- (optional) Beat 5: <one sentence>

## 4. Visual style

- **Subject framing:** centred / off-centre / handheld / static / split-screen
- **Camera energy:** name the level, "calm static", "kinetic handheld",
  "FPV push-in", "flat doc style", "motion-graphic typography only"
- **Colour and light:** 2 anchor descriptors (e.g. "warm desaturated +
  golden side-key")
- **Cut frequency:** <cuts per 10s, match section 2>
- **Style references this evokes (without copying):** max 2 (e.g.
  "Casey Neistat handheld doc", "Greg Isenberg motion-graphic kinetic
  type")
- **Typography (if motion-graphic / typeset text present):** font family
  feel (serif / sans / mono), weight, colour, scale

## 5. Audio role

- **Music:** present / absent. If present: bed style, energy curve
  (flat / rising / pulses), where it shifts.
- **VO / talking-head:** present / absent. Tone if present (calm,
  punchy, conversational, deadpan).
- **Diegetic sound:** what diegetic sound is doing work (keystrokes,
  clicks, ambient, foley, breath).
- **Audio's specific job in this video:** 1 sentence. (e.g. "The
  silence between cuts is the punchline" or "The music carries the
  emotional arc the visuals don't").

## 6. Payoff

- **What the viewer gets at the end** that justifies the whole watch.
- **The shape of the payoff:** reveal / answer / contradiction /
  surprise / earned punchline / quiet exhale / actionable step.
- **Why it's emotionally satisfying** for THIS specific audience.

## 7. CTA mechanism

- **Explicit CTA:** verbatim if present, "none" if not.
- **Implicit CTA:** what behaviour the video is engineering even without
  saying it, save, share, screenshot, comment, follow, click-bio.
  Pick ONE primary implicit CTA, don't list all five.

## 8. Why it went viral, hypothesis

2-3 sentences. NOT "great content!", name the specific mechanic.
Allowed mechanics (pick 1-2, no more):

- **Identity-confirmation:** lets the viewer feel smart / in-the-know /
  part of a tribe.
- **Status-transfer:** viewer can share to look smart/funny/early.
- **Curiosity-gap-resolution:** the video closes a gap it opened (not
  one that lingers, that's a different mechanic).
- **Visual novelty:** something the algorithm rewards because the
  thumbnail or first-frame stops the scroll.
- **Comment-bait:** a deliberate "wrong" detail or controversial line
  that drove comment velocity (the algorithm rewards engagement, not
  just watch-time).
- **Save-bait:** a screenshot-able single line or list that drove save
  velocity.

## 9. What's NOT replicable (KEEP THIS HONEST)

1-3 lines. The parts of this video that depend on the original
creator's specific identity, audience, or moment, i.e. the parts you
should NOT copy in the rebuild because they won't work for someone else.

Examples of "not replicable":

- Creator's existing audience pre-trust in their POV
- Creator's specific on-camera presence, voice cadence, face
- A current-events moment the post rode (the "what if X" prompt 2 weeks
  after the news broke)
- A platform-specific feature the creator already had access to (gold
  verification, blue-tick reach boost, paid algo boost)
- The exact wording of the hook, it's their voice, not yours
```

## Discipline rules

- **Don't praise the video. Diagnose it.** "It's just really
  well-edited" is not a deconstruction, name the specific edit choices
  (cuts per 10s, framing shifts, audio swap points).
- **If you're stuck on section 8, read what the COMMENTS would say.**
  That's usually the answer. The mechanic is whatever the comments
  reward.
- **Section 9 is the most important.** If you can't name what's NOT
  replicable, you'll let the rebuild copy the wrong things. Force
  yourself to find at least 2 unreplicable parts.
- **No vague language.** "Good pacing" → name cuts/10s. "Compelling" →
  name the mechanic. "Engaging" → name what behaviour it's engineering.

## Output destination

Write to: `<output-folder>/deconstruction.md`

Where `<output-folder>` is `~/board/_active/viral-replicator-<YYYY-MM-DD>/<creator-handle>-<post-id>/`.
