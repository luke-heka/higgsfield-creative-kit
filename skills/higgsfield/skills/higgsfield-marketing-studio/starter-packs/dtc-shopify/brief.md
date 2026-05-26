# Brief: DTC Shopify Starter Pack

Preconfigured Marketing Studio intake for a direct-to-consumer ecommerce product (skincare, supplements, apparel, kitchen gadget, $25-$120 AOV). Fill the placeholders, paste into the skill.

---

## Field 1: Product URL

```
<PASTE PRODUCT PAGE URL HERE>
```

**URL pattern guidance:**
- Must be a single product detail page (PDP), not a collection or homepage.
- Page MUST include: product name, price, hero shot, long-form description, ingredients/specs block, benefits list (3+ bullets), and at least one social-proof block (review snippet, badge, founder note).
- Shopify default theme PDPs scrape cleanly (`/products/<sku>`).
- Bare PDPs with only name + price + 1 image scrape badly. Marketing Studio loads a generic brief and the ad falls flat.
- Coach the user to point at the richest version of the page if there are multiple variants.

**Examples that scrape well:**
- `https://yourstore.com/products/hydrating-serum` (skincare PDP with ingredient story)
- `https://yourstore.com/products/protein-stack` (supplement bundle with benefits + dosing)

**Examples that scrape badly (avoid):**
- `https://yourstore.com/collections/skincare` (collection page, not a product)
- `https://yourstore.com/` (homepage)
- Headless / SPA storefronts that block scraping (Hydrogen, Next Commerce sometimes fail).

---

## Field 2: Campaign Goal

```
conversion
```

**Default for DTC:** `conversion`. Cold ecom traffic needs the full 5-clip stitch (hook to demonstrate to proof to social-proof to action). Awareness only works once you have warm retargeting pools.

**When to switch:**
- `awareness` if launching a brand-new product with no Meta pixel data yet.
- `retention` if running to an existing customer list (email/SMS audience) for a re-order push.

---

## Field 3: Avatar Strategy

```
custom_mint
```

**Always custom-mint for DTC.** The default Higgsfield avatar library is saturated, you will see the same 6 faces in every competitor's ad. A 1-minute custom mint via text prompt gives you a face nobody else has and meaningfully bumps CTR.

**Custom mint prompt template (edit the bracketed bits):**

```
A [age range, e.g. 28-34] [woman/man], [hair color and length], [skin tone],
[ethnicity if relevant to product avatar], [vibe: friendly girl-next-door /
gym-bro / busy-mum / quiet-aesthete], wearing [casual at-home outfit, no logos],
soft natural lighting, neutral expression, looks like a real customer not a model,
no makeup chair vibe, no studio gloss.
```

**Fill rules:**
- Avatar gender mirrors the product audience (skincare often female-skewed, supps often mixed, apparel match the SKU).
- Age = mid-customer-age, not 21 (algorithm distrusts overly young faces for category trust).
- Outfit = what your customer wears at home, not what a model wears in a campaign.

**Skip custom mint only if:** you are running cheap_test #1 and just want to validate the format mix. Re-mint before full_stitch.

---

## Field 4: Format Mix

```
UGC (hook 15s) -> Tutorial (demonstrate 15s) -> Unboxing (proof 10s) -> Product Review (social proof 15s) -> CTA (action 5s)
```

**Total duration:** 60s (45-60s is the DTC sweet spot for Meta + TikTok Shop).

**Why this mix (DTC-specific):**
- UGC hook: opens with the customer-pain-POV ("I tried 5 of these and...").
- Tutorial: shows the satisfying demo loop (cream absorbing, powder dissolving, before/after on skin). The single most-copied DTC ad pattern.
- Unboxing: ASMR-loud first-person package open. Builds tactile trust.
- Product Review: avatar-to-camera reaction shot, "I've been using this 3 weeks and here's what happened."
- CTA: direct, "Tap below to shop now" or "Link below, free shipping over $75."

**Cheap test mix:** UGC + CTA only (2 clips, ~200 credits, validates hook and offer before burning the full stitch).

---

## Field 5: Iteration Tier

```
cheap_test
```

Always start here. Validate the hook + CTA work before burning ~900 credits on the full 5-clip stitch.

Switch to `full_stitch` after cheap_test passes the post-render critic pass.

---

## Field 6: Output Folder

```
~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/
```

---

## DTC Hard Rules (Voice + Compliance)

- No medical outcome claims (cures, fixes, treats) on skincare/supps. Meta and platform compliance both auto-reject.
- No studio cinema look. Phone-shot vertical only. Algorithm demotes anything that looks like a corporate ad.
- No stock B-roll. Native-feel only.
- End on product or face, not on a "shop now" branded card. Branded cards kill native feel.
- Voice tone: casual, slightly tired, like texting a friend. Never corporate, never excited-announcer.
- No em dashes anywhere (use commas or full stops).
- Banned vocab: game-changer, 10x, crushing it, killing it, secret sauce, level up, unlock, transform.

---

## Fallback: When the URL Scraper Fails

Higgsfield's scraper rejects some domains. Known failure patterns:
- Custom Hydrogen / Next Commerce storefronts (SPA-rendered).
- Storefronts behind Cloudflare hard challenge.
- Selrai-style domains (custom CMS).
- Geo-blocked sites (some AU domains blocked from US scrape).

**If the scrape fails:**
1. Take a clean screenshot of the PDP (hero shot, price, benefits visible).
2. Open Marketing Studio Product tab, click "Manual entry".
3. Upload the hero image, paste product name + price + 3 benefits + ingredients block manually.
4. Save the manual-entry product card, proceed to format selection as normal.

The manual fallback produces the same quality output as a clean scrape, it just costs 5 extra minutes of intake.

---

## Confirm-Before-Building Restatement

Before clicking Generate on any clip, the skill restates:

```
DTC Marketing Studio campaign:
  Product: <URL>
  Goal: conversion -> mix: UGC + Tutorial + Unboxing + Review + CTA
  Avatar: custom_mint (<one-line description>)
  Tier: cheap_test, credits: ~200
  Output: ~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/

Proceed? (y/n)
```

Wait for `y`. Costs zero credits and saves a regen.
