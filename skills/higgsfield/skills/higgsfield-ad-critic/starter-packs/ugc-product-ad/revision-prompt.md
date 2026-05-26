# Revised Higgsfield prompt, UGC magnesium ad v2

Drop-in replacement for the v1 prompt in `example-ad-source.md`. Applies every action in the v1 critique directive. Skeleton 2 format.

## Revised prompt (paste into Higgsfield Seedance 2.0)

```
12 seconds 9:16, medium close-up handheld selfie style, Megan a woman in her early
30s tipping two capsules from @magnesium-bottle into her palm in the opening
two seconds with the bottle visible from frame one, then bringing the bottle
to chest height and looking directly at the camera to deliver one sentence,
sunlit modern kitchen with white marble counter and a small green plant out
of focus in the background, warm morning natural light from a window
camera-left, LOCK FRAMING medium-close shoulders up no zoom no scale change
across the clip, 50mm equivalent slightly compressed shallow depth of field
background soft, warm muted cream and brown palette with one soft sage accent
from the plant, audio: natural ambient kitchen sounds and her voiceover in
three beats, Beat 1 (0-3s, capsules tipping then looking to camera): "Three
weeks of this and I'm sleeping through the night for the first time in a
year." Beat 2 (3-9s, bottle held to chest, looking at camera): "I tried four
sleep aids before this. This is the only one that doesn't leave me groggy."
Beat 3 (9-12s, direct to camera, bottle held visible): "Tap shop, $45,
free shipping over $75." product @magnesium-bottle clearly visible in hand
from frame one and held through the runtime, EXCLUDE: dolly shots crane shots
tripod stability stock-photo poses watermark logo bug studio lighting 4K
cinema look perfect skin head enlarging scale changes face morphing extra
fingers sixth finger hand glitch
```

## Diff vs v1

What changed, line by line.

### Hook (0-3s)

- **Before:** "Hey guys so I've been using this magnesium for about three weeks now and honestly my sleep is so much better"
- **After:** "Three weeks of this and I'm sleeping through the night for the first time in a year."
- **Why:** Names the specific outcome (sleeping through the night) and the specific timeframe (a year) in the first 3 seconds. Drops the soft creator opener. Survives a sound-off scroll if paired with the matching CapCut text overlay.

### Shot ordering

- **Before:** Cap-twist first, capsules second, face third.
- **After:** Capsules tipping into palm is the opening frame. Cap-twist is implied, not shown. Face arrives at 0:03 after the satisfying motion has done its job.
- **Why:** The capsule-tip is the highest-visual-energy moment in the spot. Moving it from 0:02-0:04 to 0:00-0:02 puts the strongest visual on the hook beat.

### Framing constraints

- **Before:** "medium close-up handheld selfie style" (no scale-change constraint).
- **After:** "LOCK FRAMING medium-close shoulders up no zoom no scale change across the clip" plus negative constraints "head enlarging scale changes face morphing".
- **Why:** Fixes the SHOW-STOPPER head morph at 0:03-0:04 in v1. Without an explicit lock, Seedance interpolates a subtle scale change during the bottle-twist motion. Naming it in the prompt suppresses it.

### Body line (3-9s)

- **Before:** "honestly my sleep is so much better" (vague claim).
- **After:** "I tried four sleep aids before this. This is the only one that doesn't leave me groggy."
- **Why:** Replaces a generic claim with a specific story (four prior attempts + a specific differentiator). Closes the trust gap a cold-traffic viewer brings to a $45 supplement.

### CTA (9-12s)

- **Before:** No CTA. Cut to black.
- **After:** "Tap shop, $45, free shipping over $75."
- **Why:** v1 had no instruction for the viewer. The new CTA names the action (tap shop), the price ($45), and the offer (free shipping over $75). Lands in the final 3 seconds when intent is highest.

### Negative constraints

- **Added:** "head enlarging scale changes face morphing extra fingers sixth finger hand glitch"
- **Why:** Names the three artifacts the v1 render produced. Higgsfield Seedance honours named negative constraints more reliably than generic "no AI artifacts" language.

## CapCut finishing notes

This revision targets four CapCut steps in addition to the re-render:

1. Add a 0:00-0:03 text overlay of the hook line (so sound-off viewers get the hook).
2. Add a 0:09-0:12 text overlay of the CTA line.
3. Optional ADD_BROLL at 0:11, 1.5s phone-home-screen at 6:47am to back the "sleeping through the night" claim.
4. Trim any dead air at the head and tail to 0.2 seconds max.

Reference `~/.claude/skills/higgsfield/skills/shared/capcut-finishing.md` for the universal recipe.

## Expected re-critique result

If this revision is rendered and re-fed into `higgsfield-ad-critic`, the predicted verdict is SHIP, with the only remaining note being a check on Megan's hand at 0:11 for the sixth-finger artifact (the negative constraint should suppress it, but it is the highest-risk frame in the new render).
