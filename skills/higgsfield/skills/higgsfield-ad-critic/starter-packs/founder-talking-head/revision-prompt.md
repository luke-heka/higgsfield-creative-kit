# Revised Higgsfield prompt, coach talking head v2

Drop-in replacement for the v1 prompt in `example-ad-source.md`. Applies every action in the v1 critique directive. Skeleton 2 format.

## Revised prompt (paste into Higgsfield Seedance 2.0 or Cinema Studio)

```
15 seconds 9:16, medium close-up locked-off talking head, James a man in his
mid 30s sitting at a home office desk in a navy crewneck delivering a
single-take pitch to camera with NATURAL eye contact (breaking eye contact
briefly at 0:05 and 0:11 to access language) and ONE small laugh-break at
the start of beat 2, home office setting with one large green pothos plant
out of focus camera-right and a window with sheer curtains camera-left,
mixed daylight from the window and a soft fill from a desk lamp camera-right,
locked-off with very slight natural breathing motion no zoom no pan, 50mm
equivalent shallow depth of field background soft, neutral warm palette
navy crewneck cream walls one green plant accent, audio: clean voiceover
delivered in three beats with explicit pacing, Beat 1 (0-4s, steady eye
contact): "If you're a coach stuck under ten thousand a month it's almost
always because you're trying to learn everything when you should be picking
one offer and one channel." Beat 2 (4-9s, small laugh-break on "honestly"
at 0:04, brief eye-break at 0:05): "Honestly, inside the cohort we strip
your business back to one thing [0.4s pause] and scale it." Beat 3 (9-15s,
brief eye-break at 0:11, volume drops 10% on CTA): "Search jamescoach dot
com slash cohort, the first lesson is free." product not visible coach
face-only spot, EXCLUDE: dolly shots crane shots gimbal moves stock-office
sets logo bug watermark green screen background plastic studio look perfect
skin bookshelf bookcase books behind subject robotic blink cadence
unbroken eye contact extra fingers hand glitch
```

## Diff vs v1

What changed, line by line.

### Delivery direction (the biggest change)

- **Before:** Implicit. The prompt described setting and dialogue but gave Higgsfield no performance direction. The render defaulted to flat, unbroken, even-paced delivery.
- **After:** Explicit three-beat structure with named eye-breaks (0:05 and 0:11), one laugh-break (start of beat 2), one 0.4s mid-sentence pause (after "one thing"), and a 10% volume drop on the CTA.
- **Why:** Higgsfield Seedance 2.0 and Cinema Studio honour delivery direction when it is written into the audio block as specific timings. Without these notes, the render produces the AI-tell of even pacing and unbroken eye contact.

### Background

- **Before:** "wooden bookshelf out of focus behind him".
- **After:** "one large green pothos plant out of focus camera-right and a window with sheer curtains camera-left".
- **Why:** The bookshelf-behind-coach frame is the most-copied in the category and the algorithm pattern-matches it as AI. The pothos-and-window frame is rarer in 2026 coach Reels and lifts first-3-second retention.

### Negative constraints

- **Added:** "bookshelf bookcase books behind subject robotic blink cadence unbroken eye contact extra fingers hand glitch".
- **Why:** Names the three v1 artifacts (background, blink cadence, hand glitch) plus the structural fail (unbroken eye contact). Higgsfield honours these named constraints reliably.

### Script (beat 2 lightly rewritten)

- **Before:** "Inside the cohort we strip your business back to one thing and scale it."
- **After:** "Honestly, inside the cohort we strip your business back to one thing [0.4s pause] and scale it."
- **Why:** Adds the "honestly" laugh-break opener (a real founder language tic) and the explicit comma-pause that the v1 render flattened.

### CTA

- **Before:** "DM me the word COHORT if you want the details."
- **After:** "Search jamescoach dot com slash cohort, the first lesson is free."
- **Why:** Replaces a DM-bait CTA (algorithmically demoted on TikTok and Reels) with a free-resource CTA. Same downstream outcome (the page can run the ManyChat keyword flow or capture an email) without the demotion penalty.

### Hook beat (visible-overlay note)

- The v1 critique called for an on-screen text overlay of the hook ("Coach stuck under $10K/mo?") for sound-off viewers. The Higgsfield prompt itself does NOT render text overlays. This is a CapCut step listed in the finishing notes below.

## CapCut finishing notes

This revision targets four CapCut steps in addition to the re-render:

1. **0:00-0:03 hook overlay.** Text overlay: "Coach stuck under $10K/mo?" Fraunces typeface, white on black box, bottom third. Lifts sound-off retention.
2. **0:09-0:09.5 proof B-roll.** 0.5-second cutaway of a Stripe dashboard screenshot or a named-client text message. Backs the "scale it" claim. Sourced from the coach's real revenue dashboard, not stock.
3. **0:12-0:15 CTA overlay.** Text overlay: "jamescoach.com/cohort". Matches the voiceover for sound-off viewers.
4. **Audio polish.** -3dB compression on the voice track, room-tone fade at head and tail, no music.

Reference `~/.claude/skills/higgsfield/skills/shared/capcut-finishing.md` for the universal recipe.

## Expected re-critique result

If this revision is rendered and re-fed into `higgsfield-ad-critic`, the predicted verdict is SHIP. The remaining risk points are:

- The eye-break at 0:05 has to look natural, not mechanical. If Higgsfield renders it as a head-turn-then-snap-back, re-render with a softer note: "soft glance down then back up".
- The 0.4s pause after "one thing" is the highest-precision audio direction in the prompt. If Higgsfield ignores it, the fallback is to render the line as two separate chunks and add the pause in CapCut.
