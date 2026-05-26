# Revised Higgsfield prompt, ClipQueue motion-graphic v2

Drop-in replacement for the v1 prompt in `example-ad-source.md`. Applies every action in the v1 critique directive. Vibe Motion format. Compressed from 20s to 15s.

## Revised prompt (paste into Higgsfield Vibe Motion)

```
15 seconds 9:16 motion-graphic explainer for a micro-SaaS called @ClipQueue
(a one-click TikTok clip scheduler), open on a stopwatch counting up from
0:00 paired with text overlay "Scheduling TikToks the slow way: 20 minutes
per clip" for the first 3 seconds, then split-screen with painful-old-way
on the LEFT (compressed to 3 seconds) and ClipQueue UI on the RIGHT
revealing at 0:06 (the aha-moment), voiceover narration in three beats,
Beat 1 (0-3s, stopwatch animates from 0 to 20 minutes in fast-forward,
text overlay "20 minutes per clip" visible): "Scheduling TikToks the slow
way takes twenty minutes per clip. Notion, Sheets, the upload page,
copying thumbnails, typing captions, setting times." Beat 2 (3-6s,
painful-old-way side animates fast through three tab-switches, transition
at 0:5.5 to ClipQueue dashboard on the right, left side fades to gray):
"What if it only took ten seconds." Beat 3 (6-10s, ClipQueue dashboard
full-screen with a stopwatch showing 10 SECONDS held visible from 0:06
to 0:08, then a row of clips with one "schedule all" button click, all
clips show green scheduled state in 1.5 seconds, optional Product Hunt
badge cutaway at 0:09 for 0.5s): "ClipQueue does all of that from one
dashboard. Ten seconds, not twenty minutes." Beat 4 (10-15s, pricing card
animates in showing nineteen dollars a month with free-tier callout, then
fades to full-screen URL overlay clipqueue.app for 1.5 seconds at 0:13):
"Free for ten clips at clipqueue dot app. No card needed." typography:
SF Mono for UI labels and SF Pro for voiceover overlay text, large
display weight for the stopwatch numbers, palette: cream background
#F8F4ED, soft black UI text #1A1A1A, single brand purple accent #7B61FF
for ClipQueue elements, one accent red #E14B4B for the painful-old-way
stopwatch numbers, audio: clean voiceover, no music on beat 1 to let the
stopwatch tick land, soft lofi instrumental enters at 0:03 and holds,
EXCLUDE: stock explainer-video corporate look 3D character animation
cartoon mascot generic AI-powered language fake screen mockups slow
linear animation easings beat-3 holding past 0:10 vague "link in bio"
CTAs
```

## Diff vs v1

What changed, line by line.

### Runtime

- **Before:** 20 seconds.
- **After:** 15 seconds.
- **Why:** Every beat in v1 was approximately 60% longer than it needed to be. The 15-second cut keeps every story beat but moves the aha-moment from 0:11 to 0:06 (inside the SaaS-explainer retention window).

### Hook (0-3s)

- **Before:** Cursor opens a Chrome tab. No on-screen text. Voiceover prelude.
- **After:** Stopwatch counts from 0:00 with text overlay "Scheduling TikToks the slow way: 20 minutes per clip". Voiceover lands the same beat as the visual.
- **Why:** The single highest-leverage fix in the entire revision. Visual + text + voiceover land at the same moment so a sound-off viewer is qualified by 0:02.

### Painful-old-way side

- **Before:** 8 seconds of slow tab-switching, copy-paste, caption typing.
- **After:** 3 seconds of fast-forward tab-switches. Voiceover names the same stack but the visuals move at 2.5x speed.
- **Why:** The painful-old-way side is context, not story. It earns 3 seconds, not 8.

### Aha-moment

- **Before:** Lands at 0:11.
- **After:** Lands at 0:06, held with a stopwatch overlay showing "10 SECONDS" through 0:06-0:08.
- **Why:** The stopwatch overlay is the visual punchline the voiceover already promises. Without it, sound-off viewers miss the entire point.

### Body line (beat 2 rewrite)

- **Before:** "ClipQueue queues, captions, and schedules every TikTok from one dashboard."
- **After:** "ClipQueue does all of that from one dashboard. Ten seconds, not twenty minutes."
- **Why:** Anchors the benefit (time saved) instead of listing features (mechanism). Voice-true for an indie-hacker audience.

### CTA

- **Before:** "Link in bio."
- **After:** "Free for ten clips at clipqueue dot app. No card needed."
- **Why:** Names the URL (works on X, Product Hunt, Indie Hackers, not just IG and TikTok). Names the trial scope (10 clips). Removes the friction signal (no card). URL renders as a 1.5s full-screen text overlay at 0:13.

### Proof element

- **Added:** Optional Product Hunt badge cutaway at 0:09 for 0.5 seconds.
- **Why:** v1 had no "this tool is alive" signal. A Product Hunt rank, Indie Hackers user count, or MRR figure closes the trust gap indie buyers bring to a $19/mo unknown SaaS.

### Negative constraints

- **Added:** "slow linear animation easings beat-3 holding past 0:10 vague link in bio CTAs"
- **Why:** Names the three structural failures in v1 (slow easings, late aha, vague CTA) so Vibe Motion does not reproduce them.

## CapCut finishing notes

Vibe Motion renders most of this in-engine, but two CapCut steps still apply:

1. **Audio sweetening.** -3dB compression on the voiceover, lofi instrumental ducked under voice by 12dB, no music in the first 3 seconds so the stopwatch tick is audible.
2. **End card hold.** Hold the URL frame for an extra 0.3 seconds at 0:14.7 before fade-to-end. Lets the URL imprint.

Reference `~/.claude/skills/higgsfield/skills/shared/capcut-finishing.md` for the universal recipe.

## Expected re-critique result

If this revision is rendered and re-fed into `higgsfield-ad-critic`, the predicted verdict is SHIP. The remaining risk points are:

- The fast-forward animation on the painful-old-way side (0:00-0:03) has to be readable, not blurred. If Vibe Motion renders the tab-switches as a smear, slow them slightly or add a single 0.3s pause at 0:01.5 on the most relatable step (the copy-paste from Sheets).
- The stopwatch hold from 0:06-0:08 is the highest-leverage frame in the whole spot. If Vibe Motion under-emphasises the "10 SECONDS" text, increase the type size to 240pt and hold for a full 2.5 seconds.
