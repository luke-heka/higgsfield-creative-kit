# DTC E-commerce Starter Pack

**Built for:** physical-product DTC brands selling $25–$120 AOV (supplements, skincare, apparel, home, food). Tested against the patterns in the 2026 starter-pack industry research.

**What this pack ships:**
- `brief.md`, a preconfigured 5-chunk mid-funnel-punchy multi-chunk-script intake with the DTC avatar and bathroom-or-kitchen aesthetic pre-locked
- `prompts.md`, 3 paste-ready Seedance 2.0 chunk prompts (hook, solution, CTA)
- This README

**Time:** 60 to 90 minutes from product photo to finished MP4 on a clean run.

**Credits:** ~28 credits per ad on Plus plan ($49/mo), budget 1.5× = ~42 credits for fail-buffer.

---

## 60-second how-to

### Step 1, edit 5 to 9 fields in `brief.md`

Open `brief.md` and replace every `{{VARIABLE}}` with your brand's value. The 5 fields you MUST edit:

1. `{{BUSINESS_NAME}}`, your brand
2. `{{PRODUCT_NAME}}`, the SKU
3. `{{OFFER}}`, price + shipping anchor
4. `{{HERO_BENEFIT}}`, the one outcome in plain words
5. `{{SHIPPING_URL}}`, the CTA destination

Optional polish:
6. `{{BEFORE_PAIN}}`, buyer's painful before-state
7. `{{AFTER_RESULT}}`, the specific noticed change
8. `{{INGREDIENT_OR_MECHANISM}}`, the named "why it works"
9. `{{PRODUCT_TAG}}`, Higgsfield Element tag (`@bottle`, `@serum`, `@jar`, etc.)

### Step 2, pre-mint the product image

Use Nano Banana 2 or GPT Image 2.0 to render the product on a clean white background. Save to `~/board/_active/ugc-ads-<YYYY-MM-DD>/00-product-still.png`. Upload to Higgsfield → Elements → tag as your `{{PRODUCT_TAG}}`.

### Step 3, invoke the parent skill

Run the `higgsfield-ugc-ads` pipeline with this pack's `brief.md` as the Phase-0 intake:

```
/skill higgsfield-ugc-ads
```

Paste the contents of `brief.md` when prompted. The skill will load the character_lock + universal_directions + 5 chunks, run the Phase 1 to 8 pipeline, and produce a finished 1080p MP4.

### Step 4, render the 5 chunks

For each chunk, paste the matching block from `prompts.md` (chunk 1, 3, 5 are pre-written here; chunks 2 and 4 are derived by the parent skill from `chunk-prompt-template.md`). Toggle the Element tag on or off per chunk per the brief.

### Step 5, assemble in CapCut

Follow `../shared/capcut-finishing.md`. Auto-captions on. Tight cuts. Export 1080p H.264 MP4.

### Step 6, ship-gate

Run the final caption and on-screen text through `content-engine` and `humanizer`. Both must PASS before posting.

---

## What this pack will NOT do for you

- Won't fix a bad product photo. Render the source clean before tagging.
- Won't write medical or cure claims. The brief is compliant-by-default; do not edit it to introduce them.
- Won't film a real-person testimonial. This is an AI-rendered UGC ad, see `../shared/disclosure.md` for platform disclosure rules.
- Won't generate copy for the IG caption itself. That's `ad-creative`'s job, invoke it after rendering.

---

## When to swap to a different pack

| If your business is... | Use this instead |
|------------------------|------------------|
| A personal trainer or fitness coach | `../personal-trainer/` |
| A plumber, sparky, cafe, salon, restaurant | `../local-service-trade/` |
| A B2B SaaS / coach / course / real estate | use the parent skill's default flow (no starter pack covers this yet) |

---

## Compliance summary (read before editing copy)

- **No medical claims.** "Treats, cures, fixes, heals, clinically proven", banned in this pack.
- **No outcome guarantees.** "Guaranteed results", "you will lose N kg", "money-back", banned.
- **No "shop now" closing card.** End on product in hand.
- **No banned vocab** ("game-changer", "10x", "unlock", "transform", "revolutionary"), the ship-gate hard-fails.

---

## Credit estimate

| Item | Credits |
|------|---------|
| 5 chunks × ~5 credits each on 720p Plus plan | 25 |
| 1.5× regenerate buffer (Seedance ~30% first-pass fail) | +13 |
| Product still on Nano Banana 2 (Phase 1) | 0 on Ultra, 3 on Plus |
| Character reference on GPT Image 2.0 (Phase 2) | 0 on Ultra, 5 on Plus |
| **Total budget** | **~28 to 42 credits** |

Plus plan ($49/mo annual) gives 1,000 credits/mo and 4-parallel video, enough for ~24 ads/mo at this budget. Ultra plan ($99/mo annual) gives 3,000 credits/mo and 8 on 8 parallel.
