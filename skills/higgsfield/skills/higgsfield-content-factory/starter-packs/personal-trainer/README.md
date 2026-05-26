# Personal Trainer Starter Pack

60-day Instagram carousel calendar for solo PTs and small-group coaches
in the AU/NZ market. 40 carousels rendered by `carousel-generator`, with
Higgsfield supplying supporting imagery only where needed.

---

## What you'll edit (3-5 fields max)

Open `brief.md`, fill in:

1. `trainer_name`, `business_name`, `location` (suburb + city)
2. `training_modality` (1:1 in-person / online / small-group / hybrid)
3. `signature_method_name` + `price_point`
4. `client_avatar` (one sentence, the specific person you train)
5. `hero_outcome` + `transformation_timeframe` (the non-scale change at
   the N-week mark)

Everything else has sensible AU-market defaults you can leave alone.

---

## What to expect

- 40 finished carousels (8 batches of 5) in a dated folder under
  `~/board/_active/content-factory-<DATE>/`.
- Each carousel has slide PNGs (rendered by `carousel-generator`), a
  paste-ready Instagram caption in AU English, and a hashtag pack.
- Template mix: 30% mistakes, 25% tips, 20% case-study, 15% myth-bust,
  10% cheat-sheet. Locked by `brief.md`.
- Each batch needs your "yes proceed" before the next batch runs. You
  can stop or rescope between batches.

---

## Estimated cost

- **Slide rendering: $0.** `carousel-generator` renders every slide
  locally via Puppeteer + Manrope.
- **Supporting images: ~5 Higgsfield credits per image** (GPT Image 2.0)
  or ~3 credits (Nano Banana 2). Most case-study and mistakes carousels
  need 1 supporting image.
- **Typical batch (5 carousels):** 15-25 credits = roughly $1-$1.50 USD.
- **Full 60-day calendar:** ~120-200 credits = roughly $8-$12 USD.

---

## How to invoke

```
/higgsfield-content-factory personal-trainer
```

The factory will:

1. Confirm your brief variables.
2. Run Stage 1 (research trending PT content in your niche).
3. Run Stage 2 (plan 60-day calendar). You approve.
4. Run Stage 3 (generate batch 01). You approve. Then batch 02. And so
   on.
5. Optionally hand off to `omnisocials` for scheduling across IG +
   TikTok + Threads.
6. Emit a credit-spend vs agency-cost report at the end.

---

## When NOT to use this pack

- Registered dietitian, physio, or rehab specialist, the compliance
  overlay is different, ask for a custom brief.
- High-ticket coaching ($5K+), use the coach starter pack when shipped.
- Gym chain or franchise marketing, different content strategy.
- You don't have a real client transformation, either get one with
  permission first or drop the case-study slots from the rotation.

---

## Files in this pack

- `brief.md`, preconfigured intake, edit the variables here.
- `prompts.md`, 3 ready-to-render Higgsfield image prompts.
- `README.md`, this file.
- `sample/`, placeholder for sample rendered output.
