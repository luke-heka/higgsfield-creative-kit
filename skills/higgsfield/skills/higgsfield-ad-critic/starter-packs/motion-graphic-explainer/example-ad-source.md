# Example ad source, motion graphic explainer (SaaS / indie hacker)

## What this represents

A vertical motion-graphic explainer for a micro-SaaS at $19/mo. No founder face, no UGC creator. The video shows the painful old way (multiple browser tabs, a spreadsheet, a Slack message) on the left half of the screen, then a clean before-after cut to the SaaS on the right half doing the same task in one click. Voiceover narrates the "what if this only took 10 seconds" beat.

This is the dominant SaaS launch-video format on Indie Hackers, Product Hunt, and X in 2026. The Higgsfield path is Vibe Motion (the code-based graphics renderer), not Seedance, because the visuals are screen-recordings and UI motion, not pixel-prediction of real-world footage.

The prompt below renders a representative bad-but-shippable first pass. The visual story works in concept, but the pacing is far too slow: the painful-old-way half holds for 8 seconds when it should be 3, and the SaaS-aha moment lands at 0:11 when it should land at 0:06. Time-to-aha is the single most-tracked metric for SaaS launch videos and this v1 fails it.

Render this prompt in Higgsfield Vibe Motion to produce an MP4 you can feed into `higgsfield-ad-critic`. The sample critique in `critique.md` is written against the version of this render with the predictable failure mode (slow pacing, late aha-moment, vague CTA).

## Higgsfield rebuild prompt (Vibe Motion format)

```
20 seconds 9:16 motion-graphic explainer for a micro-SaaS called @ClipQueue
(a one-click TikTok clip scheduler), split-screen with painful-old-way on
the LEFT half and ClipQueue UI on the RIGHT half, voiceover narration in
three beats, Beat 1 (0-8s, painful-old-way side animates): cursor opens
Chrome, switches between three tabs (Notion, Google Sheets, TikTok upload
page), copies a thumbnail from Sheets, pastes into TikTok upload, types
a caption, sets a schedule time, all at realistic typing speed. Voiceover:
"If you're scheduling TikToks the slow way you're opening Notion, then
Sheets, then the TikTok upload page, copying thumbnails, typing captions,
setting times. Twenty minutes per clip." Beat 2 (8-15s, ClipQueue UI
animates on the right side, left side fades to gray): ClipQueue dashboard
appears, shows a row of clips with a single "schedule all" button,
button click animation, all clips show green scheduled state in 2 seconds.
Voiceover: "What if it only took ten seconds. ClipQueue queues, captions,
and schedules every TikTok from one dashboard." Beat 3 (15-20s, ClipQueue
full-screen, no split): pricing card animates in showing nineteen dollars
a month, then fades to URL. Voiceover: "Free for ten clips, nineteen
dollars a month for unlimited. Link in bio." typography: SF Mono for UI
labels and SF Pro for the voiceover overlay text, palette: cream
background #F8F4ED, soft black UI text #1A1A1A, single brand purple accent
#7B61FF for the ClipQueue brand color, audio: clean voiceover, no music
on beat 1, soft lofi instrumental enters at 0:08, EXCLUDE: stock
explainer-video corporate look 3D character animation cartoon mascot
generic AI-powered language fake screen mockups
```

## Variables used (for adapting to other SaaS offers)

- `product_name`: ClipQueue (swap for your micro-SaaS)
- `one_line_pitch`: one-click TikTok clip scheduler (swap for your pitch)
- `incumbent_competitor`: Notion + Sheets + TikTok upload page (name the actual stack the avatar is replacing)
- `primary_use_case`: scheduling TikToks (swap for the avatar's actual workflow)
- `pricing_tier`: free for 10 clips, $19/mo unlimited (swap for your tiers)
- `hero_feature`: one-click "schedule all" (swap for your aha-moment feature)

## Why this ad is a good critique target

Every failure mode that wrecks SaaS motion-graphic explainers on first pass:

1. **Pacing too slow.** The painful-old-way side holds for 8 seconds. The aha-moment lands at 0:11. SaaS launch videos that delay the aha past 0:06 lose ~40% of viewers before it lands (per Senja and TLDL 2026 indie-hacker creator data).
2. **No on-screen aha caption.** The voiceover delivers "what if it only took ten seconds" but the UI does not show a stopwatch or a side-by-side time count. Sound-off viewers miss the entire payoff.
3. **Vague CTA.** "Link in bio" is the weakest possible CTA for a micro-SaaS launch. Should name the URL.
4. **No proof element.** The video shows the UI but does not name a user count, an MRR figure, or a Product Hunt rank. Indie buyers need the "this tool is alive" signal.
5. **Pricing buried in beat 3.** A SaaS at $19/mo should anchor the price earlier so the viewer is qualified before the CTA.

## Intent brief to pass into the critic

When you hand the rendered MP4 to `higgsfield-ad-critic`, use this intent brief:

> Motion-graphic launch video for a $19/mo micro-SaaS that schedules TikToks from one dashboard. Target is indie-hacker and solo-creator avatars currently using a Notion+Sheets+manual-upload stack. Drive cold-traffic free-trial signups via a single URL. This is iteration 1, intended for X, Product Hunt, Indie Hackers, and IG Reels. Note for the critic: this is a Vibe Motion render, skip Section 3 (visual artifacts) per Pattern D in the parent skill.
