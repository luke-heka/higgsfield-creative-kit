# Real Estate Agent Starter Pack

60-day Instagram carousel calendar for solo real estate agents and small
teams owning one or two AU suburbs. 40 carousels rendered by
`carousel-generator`, with Higgsfield supplying supporting imagery only
where needed.

---

## What you'll edit (3-5 fields max)

Open `brief.md`, fill in:

1. `agent_name`, `agency`, `suburb` (the one you own), `state`
2. `price_band` + `typical_property_type` (your patch's price range and
   the home style you sell most)
3. `USP` (one sentence, why a vendor or buyer should pick you locally)
4. `lead_magnet` + `lead_magnet_keyword` (e.g. "Last 5 sales on your
   street" / "STREET")
5. `recent_comp_address` (one real recent sale you have permission to
   reference, used as anchor for case-study slots)

Everything else has sensible AU-market defaults you can leave alone.

---

## What to expect

- 40 finished carousels (8 batches of 5) in a dated folder under
  `~/board/_active/content-factory-<DATE>/`.
- Each carousel has slide PNGs (rendered by `carousel-generator`), a
  paste-ready Instagram caption in AU English, and a hashtag pack.
- Template mix: 30% case-study, 25% tips, 20% cheat-sheet, 15%
  myth-bust, 10% mistakes. Locked by `brief.md`.
- Each batch needs your "yes proceed" before the next batch runs. You
  can stop or rescope between batches.

---

## Estimated cost

- **Slide rendering: $0.** `carousel-generator` renders every slide
  locally via Puppeteer + Manrope.
- **Supporting images: ~5 Higgsfield credits per image** (GPT Image 2.0)
  or ~3 credits (Nano Banana 2) or ~7 credits (Flux for property hero).
  Most case-study carousels need 1 supporting image.
- **Typical batch (5 carousels):** 15-25 credits = roughly $1-$1.50 USD.
- **Full 60-day calendar:** ~120-200 credits = roughly $8-$12 USD.

---

## How to invoke

```
/higgsfield-content-factory real-estate-agent
```

The factory will:

1. Confirm your brief variables.
2. Run Stage 1 (research trending real estate content in your suburb /
   adjacent suburbs).
3. Run Stage 2 (plan 60-day calendar). You approve.
4. Run Stage 3 (generate batch 01). You approve. Then batch 02. And so
   on.
5. Optionally hand off to Meta MCP or `omnisocials` for scheduling.
6. Emit a credit-spend vs agency-cost report at the end.

---

## When NOT to use this pack

- You don't have a defined geographic patch (one or two suburbs you
  own), pick a patch first.
- US post-NAR jurisdiction with shifted buyer-rep language, ask for a
  US-post-NAR brief override before running.
- Property investor educator (not a licensed agent), use the coach
  starter pack when shipped.
- Commercial real estate, the objection set is different, ask for a
  custom brief.
- Your agency has a content compliance review process, feed captions
  through their review before scheduling.

---

## Files in this pack

- `brief.md`, preconfigured intake, edit the variables here.
- `prompts.md`, 3 ready-to-render Higgsfield image prompts (CASA-safe,
  no drone-over-private-property).
- `README.md`, this file.
- `sample/`, placeholder for sample rendered output.
