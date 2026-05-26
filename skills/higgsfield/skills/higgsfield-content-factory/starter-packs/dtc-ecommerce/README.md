# DTC Ecommerce Starter Pack

60-day Instagram carousel calendar for direct-to-consumer brands with a
$25-$120 AOV. 40 carousels rendered by `carousel-generator`, with
Higgsfield supplying supporting imagery only where needed.

---

## What you'll edit (3-5 fields max)

Open `brief.md`, fill in:

1. `brand_name`, `brand_handle`, `product_name`
2. `hero_benefit` (one sentence, the single reason people buy)
3. `price` + `aov_threshold` (free-shipping cutoff)
4. `target_concern` (the customer pain in their own words)
5. `before_pain` + `after_result` (for case-study slots)

Everything else has sensible defaults you can leave alone.

---

## What to expect

- 40 finished carousels (8 batches of 5) in a dated folder under
  `~/board/_active/content-factory-<DATE>/`.
- Each carousel has slide PNGs (rendered by `carousel-generator`), a
  paste-ready Instagram caption, and a hashtag pack.
- Template mix: 30% tips, 20% myth-bust, 20% case-study, 15% cheat-sheet,
  15% stack-reveal. Locked by `brief.md`.
- Each batch needs your "yes proceed" before the next batch runs. You
  can stop or rescope between batches.

---

## Estimated cost

- **Slide rendering: $0.** `carousel-generator` renders every slide
  locally via Puppeteer + Manrope.
- **Supporting images: ~5 Higgsfield credits per image** (GPT Image 2.0)
  or ~3 credits (Nano Banana 2). Most carousels need 0-1 supporting
  images.
- **Typical batch (5 carousels):** 10-15 credits = roughly $0.60-$1
  USD.
- **Full 60-day calendar:** ~80-120 credits = roughly $5-$8 USD.

If a batch needs no supporting images (most tips and myth-bust slots),
that batch is free.

---

## How to invoke

```
/higgsfield-content-factory dtc-ecommerce
```

The factory will:

1. Confirm your brief variables.
2. Run Stage 1 (research) using `apify-content-analytics` if connected,
   otherwise a fixture. You approve.
3. Run Stage 2 (plan 60-day calendar). You approve.
4. Run Stage 3 (generate batch 01). You approve. Then batch 02. And so
   on.
5. Optionally hand off to Meta MCP or `omnisocials` for scheduling.
6. Emit a credit-spend vs agency-cost report at the end.

---

## When NOT to use this pack

- Luxury brand ($500+ AOV): different objection set, different content.
- B2B SaaS / coaching: use `coach` or `saas` pack (when shipped).
- Regulated category (Rx, alcohol, CBD in restricted states): platform
  rules need a separate review first.
- You don't have a real customer transformation to use for case-study
  slots. Don't fabricate one.

---

## Files in this pack

- `brief.md`, preconfigured intake, edit the variables here.
- `prompts.md`, 3 ready-to-render Higgsfield image prompts.
- `README.md`, this file.
- `sample/`, placeholder for sample rendered output.
