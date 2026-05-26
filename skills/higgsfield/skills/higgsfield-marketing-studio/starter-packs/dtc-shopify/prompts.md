# Prompts: DTC Shopify Starter Pack

Three paste-ready Marketing Studio invocations. Fill the bracketed variables, paste into Claude, the skill handles the rest.

---

## Prompt 1: Cheap Test (2 clips, ~200 credits, ~15 min)

Use this FIRST. Always. Validates the hook + CTA before burning the full stitch budget.

```
Run higgsfield-marketing-studio cheap_test for this DTC product.

Product URL: <PASTE PRODUCT PDP URL>
Goal: conversion
Avatar: custom_mint
Avatar mint prompt: A [age, e.g. 28-32] [woman/man], [hair description],
  [skin tone], casual at-home vibe, wearing [outfit], soft natural light,
  looks like a real customer not a model.
Tier: cheap_test
Format mix: UGC (hook 15s) + CTA (5s)
Output folder: ~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/

Hard rules:
- No medical outcome claims.
- No em dashes.
- No banned vocab (game-changer, 10x, crushing it, killing it, secret sauce, level up, unlock, transform).
- Phone-shot vertical look only, no studio cinema gloss.
- CTA dialogue must pass content-engine + humanizer voice gates BEFORE rendering.
- If the URL scrape fails, fall back to manual product entry (screenshot + paste benefits).

Restate intent before generating any clip and wait for my "y".
```

**Tool params under the hood (Marketing Studio):**
- product_url: <user URL>
- campaign_goal: conversion
- avatar_mode: custom_mint_from_text
- resolution: 720p
- aspect: 9:16
- clip_count: 2
- formats: [ugc, cta]
- output_dir: ~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/

---

## Prompt 2: Full Stitch (5 clips, ~900 credits, ~45-60 min)

Run this AFTER cheap_test passes the critic gate.

```
Run higgsfield-marketing-studio full_stitch for this DTC product.

Product URL: <PASTE PRODUCT PDP URL>
Goal: conversion
Avatar: custom_mint (same prompt as cheap_test, lock the same face)
Avatar mint prompt: <verbatim from cheap_test, same character>
Tier: full_stitch
Format mix:
  - Clip 1: UGC (hook, 15s, role: hook)
  - Clip 2: Tutorial (demonstrate, 15s, role: demonstrate)
  - Clip 3: Unboxing (proof, 10s, role: proof, hands-only)
  - Clip 4: Product Review (social proof, 15s, role: social_proof)
  - Clip 5: CTA (action, 5s, role: action, rendered via direct Seedance)
Resolution: 1080p (all clips)
Output folder: ~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/

CTA dialogue (must pass voice gates before insertion):
"Tap below to shop now, free shipping over $75."

Hard rules:
- Same avatar locked across clips 1, 2, 4, 5 (clip 3 is hands-only, no face).
- Speed adjust 80-90% in CapCut to fix Seedance rush.
- B-roll overlay any hallucinated frames (head morphs, hand glitches).
- Caption + on-screen text MUST pass content-engine + humanizer voice gates.
- Hand final MP4 to higgsfield-ad-critic for post-render critique.

Restate intent and wait for my "y" before each clip render.
```

**Tool params under the hood (Marketing Studio + Seedance):**
- product_url: <user URL>
- campaign_goal: conversion
- avatar_mode: custom_mint_locked
- resolution: 1080p
- aspect: 9:16
- clip_count: 5
- formats: [ugc, tutorial, unboxing, product_review, cta]
- cta_render_engine: seedance_direct (Marketing Studio has no CTA dropdown)
- output_dir: ~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/

---

## Prompt 3: CTA-Only Render (1 clip, ~150 credits, ~5 min)

Use when the 5-clip stitch is mostly working but the CTA needs a re-render (wrong dialogue, wrong tone, or rushed delivery).

```
Re-render only the CTA clip for the DTC campaign at
~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/.

Avatar: same custom_mint locked face from clips 1, 2, 4.
Avatar mint prompt: <verbatim from full_stitch run>
Resolution: 1080p, 9:16, 5s
Engine: Direct Seedance (NOT Marketing Studio)

CTA prompt skeleton (from templates/cta-clip-prompt.md):
5 seconds 9:16, medium close-up handheld selfie style, [avatar
description] holding @product up to camera and pointing toward an
imaginary link below the frame while saying "Tap below to shop now,
free shipping over $75" with a warm natural smile, modern apartment
with soft natural light, golden hour 4pm warm soft light, handheld
with slight natural wobble no zoom no pan, 50mm equivalent slightly
shallow depth of field, warm muted palette cream and soft brown
natural skin texture not glossy, conversational warm tone voice clear
not rushed, product visible in frame held at chest height,
EXCLUDE em dashes in dialogue hyper-saturated colors plastic AI-glossy
skin stock photography pose

CTA copy gates:
- Passed content-engine voice gate: y/n
- Passed humanizer slop gate: y/n
- Under 7 words dialogue (avoids mouth-sync failure): y/n
- No outcome guarantees, no refund language: y/n
- No banned vocab: y/n

Save as: <output>/clip-cta.mp4 (overwrites previous CTA).

Re-run the CapCut stitch with the new CTA clip and ship.
```

**Tool params under the hood (Direct Seedance):**
- engine: seedance_2.0
- avatar_lock: <slug from full_stitch run>
- product_element_tag: @product (optional, if Element tagging is set up)
- duration_s: 5
- resolution: 1080p
- aspect: 9:16
- output_file: <output>/clip-cta.mp4

---

## Run order

1. Prompt 1 (cheap_test) -> review hook + CTA -> if passes critic, proceed.
2. Prompt 2 (full_stitch) -> review all 5 clips + final stitch -> if CTA needs work, run Prompt 3.
3. Prompt 3 (CTA re-render) only if CTA fails the critic on Prompt 2.

Never skip Prompt 1. The 30-50% failed-render overhead means a blind full_stitch is a $10 USD coin-toss.
