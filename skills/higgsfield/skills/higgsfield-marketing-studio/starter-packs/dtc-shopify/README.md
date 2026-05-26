# DTC Shopify Starter Pack

60-second how-to for the no-prompt Marketing Studio campaign on a Shopify (or any DTC) product.

---

## What you get

A finished 45-60 second vertical ad spot stitched from 5 clips (UGC hook + Tutorial demo + Unboxing proof + Product Review + CTA), voice-graded caption, and a cost log. Ready to upload to Meta Ads or TikTok Shop.

## What you need (under 60 seconds)

1. **A product PDP URL** with rich landing copy (name + price + 3+ benefits + ingredients + review block). Shopify default theme PDPs work. Bare collection pages do not.
2. **A campaign goal**. Default = `conversion`. Pick `awareness` for brand-new product launches with no pixel data, `retention` for re-order pushes to your email/SMS list.
3. **~200 credits for cheap_test** OR **~900 credits for the full stitch**. Plus plan ($49/mo, 4,000 credits) covers ~4 full stitches per month.

## How long

- Cheap test: ~15 minutes (2 clips, 720p).
- Full stitch: 30-60 minutes (5 clips, 1080p, plus CapCut assembly).

## The fields you edit in `brief.md`

Only two are strictly required:

1. **Product URL** (line 8 in `brief.md`). Paste your PDP URL.
2. **Avatar mint prompt** (line 47 area). Edit the bracketed bits (age, hair, vibe, outfit) so the avatar mirrors your real customer.

Everything else has DTC-tuned defaults (conversion goal, custom_mint avatar, 5-clip mix, cheap_test first).

## How to run it (3 steps)

1. Open `brief.md`, fill the two required fields.
2. Open `prompts.md`, copy **Prompt 1** (cheap_test), paste into Claude.
3. After cheap_test passes the critic gate, copy **Prompt 2** (full_stitch), paste, ship.

If your CTA looks weak after Prompt 2, copy **Prompt 3** (CTA-only re-render).

## Known scrape failures (and the workaround)

Higgsfield's URL scraper does not handle every storefront. Failure patterns:

- **Custom Hydrogen / Next Commerce storefronts** (single-page-app rendered, JS-heavy). Scraper sees an empty shell.
- **Cloudflare hard challenge** (some AU and EU storefronts).
- **Selrai-style domains** (custom CMS, no schema.org markup).
- **Geo-blocked sites** (a few AU domains block US scrape requests).

**Workaround (5 extra minutes):**

1. Take a clean screenshot of your PDP (hero shot + price + benefits visible).
2. In Marketing Studio, open the Product tab and click "Manual entry".
3. Upload the hero image, paste product name, price, 3 benefits, and the ingredients/specs block.
4. Save the manual-entry product card. Marketing Studio renders the same quality output as a clean scrape, you just hand-fed it the brief.

If the manual entry path is also broken, the issue is workspace-level, run the `higgsfield-apps` install ritual to reconnect.

## DTC-specific gotchas

- **No medical outcome claims** on skincare/supps. Meta auto-rejects.
- **End on product or face**, not a "shop now" logo card. Branded cards kill native feel.
- **Phone-shot vertical only**. Studio cinema look gets demoted by the algorithm.
- **CTA dialogue under 7 words** at 5s duration, otherwise the avatar's mouth desyncs.

## Output

Everything lands in `~/board/_active/marketing-studio-dtc-<YYYY-MM-DD>/`:

- `final-ad.mp4` (the ship asset)
- `caption.md` (voice-graded caption + hashtags)
- `clip-1-ugc.mp4` ... `clip-cta.mp4` (raw clips for re-editing)
- `cost-log.md` (credits burned + regen count)
- `critic-report.md` (post-render critique)

## When to come back to this pack

Each new product = new starter-pack run. Same brand can reuse the avatar Soul ID across runs by promoting the custom_mint to a Soul ID after run #1, see `higgsfield-soul`.
