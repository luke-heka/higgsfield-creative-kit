# Example ad source, UGC product ad (DTC supplement)

## What this represents

A vertical UGC-style ad for a DTC magnesium supplement brand. Single creator in a kitchen at morning, holds the bottle, tips two capsules into her palm, delivers a soft conversational line, and ends with the bottle held to camera. Shot-on-phone aesthetic, no studio gloss, no logo end card.

This is the typical $25-120 AOV DTC vertical: 12 seconds, 9:16, founder-or-creator at home, real product in real hand, conversational voiceover. Top-performing pattern on TikTok Shop and Meta Advantage+ Shopping in 2026.

The prompt below is intentionally written as a representative bad-but-shippable first-pass render. Soft opener, no scroll-stop hook, generic creator language in the first line. This is the kind of render that lands in the critique pipeline daily.

Render this prompt yourself in Higgsfield Seedance 2.0 to produce an MP4 you can feed into `higgsfield-ad-critic`. The sample critique in `critique.md` is written against the version of this render with the predictable failure modes (soft hook, head morph at 0:04, lip-sync slip at 0:10).

## Higgsfield rebuild prompt (Skeleton 2 format)

```
12 seconds 9:16, medium close-up handheld selfie style, Megan a woman in her early
30s holding @magnesium-bottle and twisting off the cap to tip two capsules into
her palm with a soft natural smile as she does it, then bringing the bottle up
to chest height and looking directly at the camera, sunlit modern kitchen with
white marble counter and a small green plant out of focus in the background,
warm morning natural light from a window camera-left, handheld with slight
natural wobble no zoom no pan, 50mm equivalent slightly compressed shallow
depth of field background soft, warm muted cream and brown palette with one
soft sage accent from the plant, audio: natural ambient kitchen sounds and
her voiceover playing over: "Hey guys so I've been using this magnesium for
about three weeks now and honestly my sleep is so much better", product
@magnesium-bottle clearly visible held in hand from 2 seconds onward, EXCLUDE:
dolly shots crane shots tripod stability stock-photo poses overlay text
watermark logo bug studio lighting 4K cinema look perfect skin
```

## Variables used (for adapting to other DTC offers)

- `brand_name`: magnesium-bottle (replace with `@your-product` tag)
- `product_name`: magnesium supplement (swap for skincare, hair, supps, apparel)
- `hero_benefit`: better sleep (swap for the single benefit you lead with)
- `founder_or_creator_name`: Megan (swap for the creator on your roster)
- `setting`: sunlit modern kitchen (swap for bathroom, bedroom, home office)
- `price_point`: not mentioned in spot, lives on the landing page
- `target_concern`: sleep + stress (swap for the avatar's actual pain)

## Why this ad is a good critique target

Every failure mode the DTC industry hits on the first pass shows up here:

1. **Soft opener.** No problem-name, no pattern-interrupt, no scroll-stop.
2. **Generic creator phrasing.** "Hey guys so I've been using" sounds like every other UGC ad in the feed.
3. **Outcome implied without proof.** "My sleep is so much better" lands as a claim, not a story.
4. **No CTA.** No instruction to the viewer at the end of the spot.
5. **Likely visual artifacts.** Head morph during the bottle-twist motion at 0:04, lip-sync slip on "honestly" around 0:10.

## Intent brief to pass into the critic

When you hand the rendered MP4 to `higgsfield-ad-critic`, use this intent brief:

> UGC ad for a magnesium sleep supplement, target is women 28-42 with on-and-off sleep issues. Drive cold-traffic add-to-cart on the $45 single bottle. This is iteration 1, shot-on-phone aesthetic, native to TikTok Shop and Meta Reels.
