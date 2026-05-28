# Worked Example, Skincare Product, 60s Conversion Stitch

A full run of the skill, end-to-end, for a fictional skincare brand
(LumenSkin Vitamin C Serum). Use this as the reference when a real
campaign briefs in.

---

## Intake

User pasted into chat:

> Use higgsfield marketing studio. Product is https://example.com/lumenskin/vitamin-c-serum, conversion campaign, female founder-style avatar. Cheap test first.

Skill restated:

```
Marketing Studio campaign:
  Product: https://example.com/lumenskin/vitamin-c-serum
  Goal: conversion → format mix: UGC + Tutorial + Unboxing + Review + CTA
  Avatar: custom_mint (female founder-style, to be minted)
  Tier: cheap_test, credits: ~200
  Output: ~/board/_active/marketing-studio-2026-05-24/

Proceed? (y/n)
```

User: `y`.

---

## Step 1, Product ingest

Marketing Studio scrape returned:

- Product name: **LumenSkin 15% Vitamin C Serum, 30ml**
- Price: AUD $89
- Benefits scraped:
  - "Brightens uneven tone in 4 weeks"
  - "L-ascorbic acid stabilised with ferulic acid"
  - "Lightweight, non-sticky finish"
  - "Cruelty-free, made in Sydney"
- Hero image: amber dropper bottle on white

Screenshot saved to `00-product-card.png`. Card looks clean.

`00-brief.md` written.

---

## Step 2, Format selection

Goal = conversion → applied the 5-clip recipe. Tier = cheap_test → over-rode to 2-clip throwaway (UGC + CTA).

`01-format-list.md`:

```markdown
# Format Mix

**Goal:** conversion
**Tier:** cheap_test

| # | Format | Duration | Role | File output |
|---|--------|----------|------|-------------|
| 1 | UGC | 15s | hook | clip-1-ugc.mp4 |
| 2 | CTA | 5s | action | clip-cta.mp4 |

**Total stitched duration:** 20s
**Avatar locked for clip 1 + CTA:** lumenskin-founder-v1
**Estimated credits:** ~200
```

---

## Step 3, Avatar mint

Tier 1 custom mint. Prompt:

```
Woman in her late 30s, light brown hair shoulder length, warm friendly
smile, natural minimal makeup, wearing a cream knit jumper, looks like a
real-life Australian skincare brand founder, not a model, not overly
polished, natural skin texture with subtle pores visible.
```

Avatar minted in 55 seconds, 50 credits. Saved to library as
`lumenskin-founder-v1`.

`00-brief.md` updated with avatar block.

---

## Step 4, Render loop (cheap_test, 2 clips)

### Clip 1, UGC (15s, 720p)

Marketing Studio settings: product LumenSkin loaded + avatar
lumenskin-founder-v1 + format UGC + 15s + 720p + 9:16. Click Generate.

Render time: 78 seconds. Cost: 75 credits.

Watch end-to-end:

- Avatar holds the dropper bottle close to camera, talks naturally
  about brightening tone, ends with a natural smile.
- One minor hallucination: at 0:09 her left hand briefly shows 6 fingers
  for ~0.3s. Noted in `cost-log.md`, covered with B-roll later (or
  accept since under 0.5s threshold).
- VO is clear, slightly rushed (will slow to 85% in CapCut).

Pass. Download as `clip-1-ugc.mp4`.

### Clip CTA (5s, 720p)

CTA copy drafted, ran through `content-engine` + `humanizer`:

- Draft 1: "Unlock brighter skin, link below to transform your routine."
- humanizer flag: "unlock", "transform" both banned.
- Rewrite: "See it for yourself, link below to shop."
- content-engine pass (sounds like your brand / natural).
- humanizer pass.

CTA prompt assembled from `templates/cta-clip-prompt.md`:

```
5 seconds 9:16, medium close-up handheld selfie style, woman in her late
30s holding @product up to the camera and pointing toward an imaginary
link below the frame while saying "See it for yourself, link below to
shop" with a warm natural smile, modern apartment with soft natural
light, golden hour 4pm warm soft light, handheld with slight natural
wobble no zoom no pan, 50mm equivalent slightly shallow depth of field,
warm muted palette cream and soft brown natural skin texture not glossy,
conversational warm tone voice clear not rushed, product visible held
at chest height, EXCLUDE em dashes in dialogue hyper-saturated colors
plastic AI-glossy skin stock photography pose
```

Note: `@product` Element was pre-uploaded (the LumenSkin amber dropper)
so the bottle in the CTA clip exactly matches clips 1's bottle.

Render time: 50 seconds. Cost: 75 credits. Pass on first try.

Download as `clip-cta.mp4`.

**Cheap_test total so far:** 50 (avatar mint) + 75 + 75 = 200 credits ≈
$2.40 USD.

---

## Step 5, Assembly (cheap_test version)

CapCut:

1. Imported clip-1 + clip-cta in order.
2. Speed adjust clip-1 to 85% (felt rushed at 100%).
3. B-roll overlay over the 0.3s hand glitch at 0:09 (used a still frame
   of the bottle on white).
4. Auto-captions, Classic preset, yellow on dark, raised 18%.
5. Exported 720p H.264 9:16 as `final-ad-cheap-test.mp4`. Duration: 20s.

---

## Step 6, Voice-grade caption

Drafted social caption + ran both gates:

- Draft: "This is a game-changer for dull skin, 10x brighter in 4 weeks!"
- humanizer: "game-changer", "10x", em dash all banned. Hard fail.
- Rewrite: "LumenSkin's Vitamin C serum, stabilised with ferulic acid, brightens uneven tone in about 4 weeks. Made in Sydney, cruelty-free, $89. Link below to try it."
- content-engine pass (no slop, no outcome guarantees).
- humanizer pass.

`caption.md`:

```markdown
# Final Caption + CTA

## Social caption

LumenSkin's Vitamin C serum, stabilised with ferulic acid, brightens
uneven tone in about 4 weeks. Made in Sydney, cruelty-free, $89. Link
below to try it.

## CTA copy

See it for yourself, link below to shop.

## Hashtags

#skincare #vitaminc #australianskincare #sydneymade #crueltyfree
```

---

## Step 7, Cheap_test review (human gate before full_stitch)

Watched `final-ad-cheap-test.mp4` end-to-end on phone, 9:16, sound on.

Checks:

- Hook lands within first 2 seconds? Yes, she opens with "If your skin
  looks flat by 3pm..."
- Product clearly visible? Yes, bottle held at chest height for most
  of the UGC clip.
- CTA legible? Yes, captions help, voice clear, link cue obvious.
- Hallucinations? One covered, none catastrophic.
- Voice grade? Caption + CTA both passed gates.
- Brand consistency? Avatar and product both feel cohesive.

Verdict: **PASS**. Approve full_stitch.

---

## Step 8, Full_stitch run (5 clips, 1080p)

Skill re-prompted user:

```
Cheap_test passed. Proceed to full_stitch?
  Tier: full_stitch, credits: ~875 ≈ $10.50
  Avatar: lumenskin-founder-v1 (already minted)
  Resolution: 1080p
  Same product card.
Proceed? (y/n)
```

User: `y`.

Render loop ran clips 2-4 (Tutorial, Unboxing, Review) plus re-ran
clips 1 + CTA at 1080p. Total 5 new renders (clip 1 + CTA re-rendered at
1080p for the final, since cheap_test versions were 720p).

Per-clip credit cost at 1080p + same avatar: ~150 each. Plus 1 regen of
Clip 3 Unboxing (first render showed wrong product shape):

- Clip 1 UGC 1080p: 150 credits, pass
- Clip 2 Tutorial 1080p: 150 credits, pass
- Clip 3 Unboxing 1080p: 150 credits, FAIL (wrong bottle shape)
- Clip 3 Unboxing regen with `@product` Element forced: 150 credits, pass
- Clip 4 Review 1080p: 150 credits, pass
- Clip CTA 1080p: 150 credits, pass

Render loop subtotal: 1050 credits (875 estimated + 1 regen = 1025
actual, within 30% overhead budget).

---

## Step 9, Final CapCut assembly

Same recipe as cheap_test, scaled to 5 clips:

1. Imported in order: UGC → Tutorial → Unboxing → Review → CTA.
2. Speed adjust each to 85%.
3. B-roll overlay covers: 1 minor hand glitch in Clip 2, 1 frame face
   wobble in Clip 4.
4. Auto-captions, Classic preset, yellow on dark, raised 18%.
5. Exported 1080p H.264 9:16 as `final-ad.mp4`. Duration: 60s.

---

## Step 10, higgsfield-ad-critic (skipped, not yet built)

Placeholder written to `critic-report.md`:

```
TODO, run higgsfield-ad-critic when skill becomes available.

Manual self-review:
- Hook strength: strong (open question lands in first 2s)
- Pacing: 85% speed across all clips reads natural
- Hallucination check: 2 minor covered, 0 visible in final
- CTA legibility: pass
- Caption-VO sync: tight
- Ship readiness: yes
```

---

## Final cost log

```markdown
| Stage | Credits | USD |
|-------|---------|-----|
| Avatar mint | 50 | $0.60 |
| Cheap_test (2 clips, 720p) | 150 | $1.80 |
| Full_stitch (5 clips, 1080p) | 750 | $9.00 |
| Regens (1 Unboxing) | 150 | $1.80 |
| **TOTAL** | **1100** | **$13.20** |

**Time spent (human):** ~95 minutes total.

**Comparison:**
- Traditional UGC agency: $800-1,500 + 2 weeks
- Freelance UGC creator: $250-400 + 1 week
- Selr AI Marketing Studio skill: $13.20 + 95 min
```

---

## Ship handoff

```
~/board/_active/marketing-studio-2026-05-24/
├── 00-product-card.png
├── 00-brief.md
├── 01-format-list.md
├── clip-1-ugc.mp4
├── clip-2-tutorial.mp4
├── clip-3-unboxing.mp4
├── clip-4-review.mp4
├── clip-cta.mp4
├── final-ad.mp4         ← upload this to Meta Ads / TikTok / Reels
├── caption.md           ← paste this into post copy
├── critic-report.md
└── cost-log.md
```

User uploaded `final-ad.mp4` to Meta Ads via the `paid-ads` skill.
`~/board/_log.md` updated with the line:

```
- 2026-05-24, Marketing Studio campaign shipped: LumenSkin Vitamin C, conversion, $13.20, ~95min
```

Skill run complete.
