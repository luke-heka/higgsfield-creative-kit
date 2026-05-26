# Example ad source, founder talking head (online coach)

## What this represents

A vertical founder-to-camera ad for a $497 online coaching cohort. Coach sits at a home office desk in front of a bookshelf, leans into camera, delivers a 15-second pitch about their signature method, ends with a soft "DM me" CTA. The kind of render a coach makes when they want to qualify cold-traffic Reels viewers into a free lead magnet.

This is the typical low-to-mid-ticket coach format: 15-20 seconds, 9:16, single founder at a desk, high-conviction delivery, screen-recording or whiteboard implied in the background. The dominant signup format on coach Reels and TikTok in 2026.

The prompt below renders a representative bad-but-shippable first-pass. The voiceover is technically correct but the delivery is stiff, the eye-contact never breaks, and the energy reads as scripted-not-spoken. This is the most common failure mode for founder-talking-head renders, and the one most coaches do not catch on their own.

Render this prompt in Higgsfield Seedance 2.0 or Cinema Studio to produce an MP4 you can feed into `higgsfield-ad-critic`. The sample critique in `critique.md` is written against the version of this render with the predictable failure modes (flat delivery, no micro-expression, robotic blink cadence, soft DM-bait CTA).

## Higgsfield rebuild prompt (Skeleton 2 format)

```
15 seconds 9:16, medium close-up locked-off talking head, James a man in his
mid 30s sitting at a home office desk in a navy crewneck delivering a
single-take pitch to camera with steady eye contact and one or two hand
gestures, home office setting with a wooden bookshelf out of focus behind
him and one warm desk lamp camera-right, mixed daylight from a window
camera-left and a soft fill from the lamp, locked-off with very slight
natural breathing motion no zoom no pan, 50mm equivalent shallow depth of
field background soft, neutral warm palette navy crewneck cream walls,
audio: clean voiceover slightly elevated conviction tone, "If you're a
coach stuck under ten thousand a month it's almost always because you're
trying to learn everything when you should be picking one offer and one
channel. Inside the cohort we strip your business back to one thing and
scale it. DM me the word COHORT if you want the details.", product not
visible coach face-only spot, EXCLUDE: dolly shots crane shots gimbal
moves stock-office sets logo bug watermark green screen background
plastic studio look perfect skin
```

## Variables used (for adapting to other coach offers)

- `coach_name`: James (swap for the actual coach)
- `niche`: coach stuck under $10K/mo (swap for the avatar's actual situation)
- `signature_method_name`: not named in v1 (swap in your method by name)
- `lead_magnet_keyword`: COHORT (swap for the keyword your ManyChat or DM flow listens for)
- `price_point`: not mentioned in spot, lives on the lead magnet page
- `transformation_timeframe`: not specified
- `hero_client_result`: not used in this version

## Why this ad is a good critique target

Every failure mode that wrecks founder-talking-head ads on first pass:

1. **Stiff delivery.** Voice is correct on paper, but the AI render reads as scripted, not spoken. No micro-expression, no breath-break, no laugh.
2. **Robotic eye contact.** James stares directly into the camera for 15 unbroken seconds. Real founders break eye contact every 4-7 seconds.
3. **Soft DM-bait CTA.** "DM me the word COHORT" is the kind of CTA TikTok actively demotes in 2026 (DM-bait detection).
4. **No proof element.** The pitch makes a claim ("strip your business back to one thing and scale it") without a single piece of evidence (number, named client, screenshot).
5. **Background is generic.** Bookshelf-behind-coach is the most-copied frame in the category and pattern-matches as AI in 2026 feeds.

## Intent brief to pass into the critic

When you hand the rendered MP4 to `higgsfield-ad-critic`, use this intent brief:

> Founder-to-camera ad for an online coaching cohort. Target is coaches stuck under $10K/mo who have bought 2-3 courses already and not finished any. Drive cold-traffic DM keyword (the word COHORT) into a ManyChat flow that delivers the cohort details. This is iteration 1, intended for Instagram Reels and TikTok.
