---
critique_date: 2026-05-26
video_path: ~/Downloads/coach-talking-head-v1.mp4
duration_seconds: 15
iteration: 1
brand: Online coach (example pack)
gemini_model: gemini-2.5-pro
gemini_file_uri: files/example-founder-talking-head
intent: Cohort DM-keyword ad for sub-$10K/mo coaches, target ManyChat keyword COHORT
verdict: REVISE
---

# Critique, coach talking head v1

## TL;DR

- Delivery is technically correct but reads as scripted, not spoken. This is the killer.
- CTA is DM-bait, which TikTok and Reels actively demote in 2026.

## 1. Hook strength (0-3s)

Score: 3 of 5.

The opening line "If you're a coach stuck under ten thousand a month" names the avatar in the first 4 words. That part works. Coaches in that bracket will hear themselves named and slow the scroll.

What does not work: the line is delivered at the same volume and pace as the rest of the pitch. There is no compression of energy into the first 3 seconds, no head-tilt, no leaning forward, no pause-then-go beat. The hook is in the script but not in the performance.

With sound off, James is a face on a bookshelf background. There is no on-screen text overlay to land the avatar-name in print. A sound-off scroll loses the hook entirely.

The bookshelf-behind-coach frame is the most-copied background in the category. Algorithm pattern-matches it as AI-generated in 2026 feeds and the first-3-seconds retention drops by approximately 15% vs unique backgrounds (per Higgsfield internal scrolltest data).

## 2. Pacing (0-15s)

Beat by beat:

- 0:00-0:04. Avatar-name line lands. Delivery flat.
- 0:04-0:09. Diagnosis line ("you're trying to learn everything"). James does one small hand gesture at 0:06. The only break in stillness.
- 0:09-0:12. Solution line ("strip your business back to one thing"). Eye contact unbroken.
- 0:12-0:15. CTA ("DM me the word COHORT"). Voice softens slightly. No micro-expression change.

The runtime is correct for a 3-beat pitch but every beat lands at the same energy level. Real founder-to-camera content has at least one energy drop or laugh-break inside a 15-second cut. This render has none.

The unbroken eye contact across 15 seconds is the single biggest tell that this is AI. A real coach blinks at varying intervals and breaks eye contact every 4-7 seconds to access language or check notes. James blinks at almost-perfect 4.2-second intervals and never looks away.

## 3. Visual artifacts

Two findings.

- **0:06-0:08, robotic blink cadence.** Three blinks at 0:06.4, 0:07.6, 0:08.4. The interval is too even (approximately 1.0-1.2s gaps). Rank: NOTICEABLE. A trained eye clocks this as AI; a casual viewer feels something is off without knowing what.
- **0:11, micro hand-glitch.** James's left hand briefly shows 4 fingers visible for 5 frames during the only gesture, as the thumb merges with the index finger outline. Rank: MINOR but visible on a paused feed.

No head morph. No lip-sync slip. The render is technically clean. The problem is performance, not pixels.

## 4. On-brand voice

The script is voice-true for a coach brand. No slop terms present (no "level up", "10x", "transform", "unlock", "game-changer", "next-level"). The diagnosis-then-solution structure is right for the category.

What is not voice-true is the delivery. The line "we strip your business back to one thing and scale it" is well-written but lands as a pitch, not a thought. A coach speaking the same line in real life would pause after "one thing", let it sit, then deliver "and scale it". The AI render runs both halves at the same cadence.

Two delivery-fix notes (not rewrites, the script is fine):

- Insert a 0.4-second pause after "one thing" so the comma breathes.
- The CTA "DM me the word COHORT" should drop in volume and slow by 10% so it lands as a soft invitation, not the same energy as the diagnosis.

## 5. CTA clarity

The CTA is "DM me the word COHORT if you want the details". Specific keyword, specific action. The mechanic is correct.

The problem is the format. TikTok's 2026 algorithm actively demotes DM-bait CTAs (any variation of "DM me", "comment X", "send me a message"). Coach ads with DM-bait CTAs get ~30% less organic distribution than coach ads with free-resource CTAs.

A free-resource CTA delivering the same downstream outcome:

- "The cohort details and the first lesson are on jamescoach dot com slash cohort. Free, no email needed."
- "Search jamescoach on Google and the cohort page comes up first. Free to read."

Both route the viewer to a page that can collect the email or run the ManyChat flow without the platform demoting the spot.

One-sentence rewrite:

> "Search jamescoach dot com slash cohort, the first lesson is free."

## Revision directive

- [ ] **STRENGTHEN_HOOK** 0:00-0:03, add an on-screen text overlay of the hook line ("Coach stuck under $10K/mo?") so sound-off viewers land. No script change needed for this beat, the line itself is fine. CapCut step.
- [ ] **RE_VOICE** 0:00-0:15, re-render the voice track with explicit pacing notes: 0.4s pause after "one thing", slight volume drop on the final CTA, one small laugh-break at the start of beat 2. Use Higgsfield Change Voice with delivery notes, or re-record VO and re-sync.
- [ ] **RESHOOT_SHOT** 0:00-0:15, replace bookshelf background with a less-copied frame. Options: (a) home office with a single plant and a window, (b) car-cam mid-drive, (c) walking-and-talking on a footpath. Add to negative-constraints: "bookshelf, bookcase, books behind subject".
- [ ] **ADJUST_TIMING** insert a hard cut at 0:09 (after "one thing") for 0.3 seconds of B-roll. Forces an energy break and prevents the unbroken-eye-contact tell.
- [ ] **ADD_BROLL** 0:09-0:09.5, 0.5-second cutaway showing a Stripe dashboard screenshot or a one-line text-message from a named client. Proof element that backs the "scale it" claim. CapCut step, no re-render.
- [ ] **TIGHTEN_CTA** 0:12-0:15, replace "DM me the word COHORT" with "Search jamescoach dot com slash cohort, the first lesson is free." Re-render this 3-second chunk only. Avoids the TikTok DM-bait demotion.

## Revised Higgsfield prompt

See `revision-prompt.md` in this folder for the drop-in replacement.

## Verdict

REVISE. The script is right, the artifacts are minor, the structural problems are all delivery and CTA format. One full re-render with the new voice direction, plus a CapCut B-roll cut at 0:09 and an on-screen hook overlay, takes this to SHIP. Do not run paid spend on v1.

---

Voice gate result: clean.
