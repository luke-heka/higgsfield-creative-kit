---
critique_date: 2026-05-26
video_path: ~/Downloads/magnesium-ugc-v1.mp4
duration_seconds: 12
iteration: 1
brand: DTC supplement (example pack)
gemini_model: gemini-2.5-pro
gemini_file_uri: files/example-ugc-product-ad
intent: UGC ad for $45 magnesium sleep supplement, women 28-42, cold-traffic ATC
verdict: REVISE
---

# Critique, UGC magnesium ad v1

## TL;DR

- Hook is soft. The first three seconds will not survive a paid feed.
- Visual artifacts at 0:04 and 0:10 are noticeable but fixable in one chunk re-render.

## 1. Hook strength (0-3s)

Score: 2 of 5.

The opening frame is a hand twisting a bottle cap. No face yet, no problem-name, no pattern-interrupt. The first audible line is "Hey guys so I've been using this magnesium for about three weeks now". That phrasing reads as a soft creator opener, not an ad hook. A viewer scrolling at speed does not get a reason to stop.

With sound off, the hook is a hand and a generic kitchen counter. There is no on-screen text overlay, no product-on-face moment, no visual cue that this is for someone with a sleep problem.

The avatar (women 28-42 with on-and-off sleep issues) is not named anywhere in the first three seconds. Top DTC supplement ads in 2026 name the pain in the hook frame ("Tired of waking up at 3am?" or "POV: you have tried five sleep aids"). This render skips that.

## 2. Pacing (0-12s)

Beat by beat:

- 0:00-0:02. Hand twists cap. Quiet, no voice, no text. Dead air for the algorithm.
- 0:02-0:04. Capsules tip into palm. The motion itself is satisfying and would be a strong cold-open if it landed at 0:00.
- 0:04-0:06. Voiceover starts mid-sentence. Bottle is now visible. This is where the actual ad begins.
- 0:06-0:09. Megan looks at camera, soft smile, delivers the claim about sleep.
- 0:09-0:12. Bottle held to chest. Cut to black.

The 12-second runtime is correct for the message, but the structure is upside-down. The satisfying capsule-tip moment lives at 0:02-0:04 where it should live at 0:00-0:02. The strongest visual is buried.

## 3. Visual artifacts

Three findings.

- **0:03-0:04, head morph.** Megan's head briefly enlarges by approximately 15% over 12 frames during the bottle-twist motion, then snaps back. Rank: SHOW-STOPPER. A viewer will clock this as AI within one watch.
- **0:09-0:10, lip-sync slip.** Mouth closes on the vowel in "honestly" while the audio still has 6 frames of phoneme remaining. Rank: NOTICEABLE.
- **0:11, hand finger count.** The hand holding the bottle to chest shows what reads as a faint sixth finger outline on the right edge for 4 frames. Rank: MINOR but visible on a paused feed.

## 4. On-brand voice

The script reads as generic creator-speak, not DTC supplement category voice. "Hey guys so I've been using" and "honestly my sleep is so much better" are the two weakest phrases. Both are pattern-matched in the feed as soft-sell influencer language and lose trust on cold traffic.

No slop terms (game-changer, level up, transform, unlock) are present. That is fine.

Two voice-true replacement lines for the same beat:

- "Three weeks of taking this before bed and I am sleeping through the night for the first time in a year."
- "I tried four sleep aids before this. The difference with this one is I do not wake up groggy."

Both keep the conversational kitchen-creator energy but trade soft language for a specific story.

## 5. CTA clarity

There is no CTA. The spot ends on the bottle held to chest and cuts to black. A viewer who likes the ad has no instruction.

For a $45 DTC ATC ad, the CTA should land in the last 1-2 seconds and be one of:

- "Link in bio, free shipping over $75."
- "Tap shop, single bottle for the first 500 orders."
- "Comment SLEEP and I will send the link."

One-sentence rewrite:

> "Tap shop, $45 for the bottle, free shipping over $75."

## Revision directive

- [ ] **STRENGTHEN_HOOK** 0:00-0:03, rewrite line and re-order shot. Open on the capsule-tip moment, not the cap-twist. Replace "Hey guys so I've been using this magnesium for about three weeks now" with one of: (a) "Three weeks of this and I am sleeping through the night for the first time in a year." (b) "I tried four sleep aids. This is the only one that does not leave me groggy." Add on-screen text overlay of the chosen line so the hook lands with sound off.
- [ ] **RESHOOT_SHOT** 0:03-0:05, head morph. Re-prompt: lock framing medium-close on shoulders up, no zoom, no scale change across the chunk. Add to negative-constraints: "head enlarging, scale changes, face morphing".
- [ ] **RE_VOICE** 0:09-0:10, lip-sync slip on "honestly". Either re-render the chunk or use Higgsfield Change Voice on that 2-second segment, then realign in CapCut.
- [ ] **ADJUST_TIMING** drop the second-half hold from 3 seconds to 1.5 seconds. The bottle is on screen long enough by 0:09.
- [ ] **TIGHTEN_CTA** 0:10-0:12, add an explicit CTA line. Suggested: "Tap shop, $45, free shipping over $75." Voiceover the line and overlay the same text on screen.
- [ ] **ADD_BROLL** 0:11, optional 1.5s CapCut overlay of a sleep-time-stamp screenshot (phone home screen at 6:47am with no notifications) to back the "sleeping through the night" claim. CapCut step, no re-render.

## Revised Higgsfield prompt

See `revision-prompt.md` in this folder for the drop-in replacement.

## Verdict

REVISE. The bones of the render are right (creator, kitchen, product visibility, conversational tone) but the hook ordering, the head morph at 0:04, and the missing CTA mean this should not go to paid spend. One re-render of chunk 1 (0:00-0:05) plus a CapCut overlay for the CTA gets this to SHIP.

---

Voice gate result: clean.
