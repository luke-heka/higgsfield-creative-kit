# Coach / Course Launch Starter Pack

A preconfigured starter pack for `higgsfield-cmo-agent`. Use this when
you're launching a coach cohort, online course, mastermind, or 1:1
coaching program and want the 8-stage campaign pipeline pre-tuned for
the coach voice, receipts-first visuals, and cart-open / cart-close
launch rhythm.

## What you get

- `brief.md`, preset Stage 0 intake. Coach voice rules, ban-list
  (no income claims, no rented luxury, no fake scarcity, no DM-bait),
  channel defaults (email + YouTube + organic IG primary), visual
  archetypes (talking-head + screen-record-teach + walking-and-
  talking).
- `prompts.md`, three paste-ready prompts: kickoff for Stage 0 to
  Stage 1, coach creative brief variant for Stage 3, coach JV /
  podcast / affiliate DM variant for Stage 6.
- `sample/`, placeholder for an example campaign run.

## When to use this pack

- You're launching a coach cohort, online course, mastermind, or
  1:1 program.
- Price band $97 to $25K (low-ticket course through high-ticket
  mastermind).
- The campaign has a defined cart open and cart close window (live
  launch model). For evergreen, run Stage 4 with a different rhythm
  but keep the rest.
- The coach is the on-camera operator (personal-brand vertical, not
  faceless).
- Language: AU or US English, the operator's call, captured at
  intake.

Don't use this pack if the brand is a physical DTC product (see
`dtc-product-drop`), a local service trade / hospitality business
(see `local-service-opening`), or a SaaS / B2B software tool.

## The 5-field brief

To run a full campaign, you need:

1. **Brand / program name** (e.g. "The Conversion Lab")
2. **Coach name + offer + price** (e.g. "Mia Reyes, The 8-Week
   Cohort, $1,997")
3. **Cart open + cart close dates** in ISO format (e.g.
   "2026-06-10 to 2026-06-17")
4. **Named method + transformation timeframe** (e.g. "The 3-Layer
   Sales Stack, 8 weeks")
5. **Hero client result with receipts**, NOT an income claim
   (e.g. "Mia's client Sara raised her discovery-call close rate
   from 22% to 61% in cohort 3, screenshots in the program page")

Optional but useful: masterclass / webinar date, target avatar in
12 words, niche, origin moment, specific plateau, real cohort cap.

## Cost

- **Documents only:** ~$0. The pipeline produces 8 markdown files,
  paste-ready Higgsfield prompts, and a Notion campaign page. No
  paid renders.
- **With renders:** $5 to $30 per campaign depending on how many
  Higgsfield previews you opt into. Coach launches typically need
  fewer renders than DTC because most assets are talking-head or
  screen-record (no AI footage needed).

## Time

- **Per full 8-stage run:** 15 to 25 minutes. Each stage saves to
  disk, you review, then the next stage dispatches.
- **First-time setup:** add ~5 minutes for capturing the brief and
  reviewing the coach-vertical priors.

## How to run

```text
Build me a complete multi-channel marketing campaign for the
{{BRAND}} {{OFFER}} launch with cart open {{CART_OPEN_DATE}} and
cart close {{CART_CLOSE_DATE}}. Use the Coach / Course Launch
starter pack at
~/.claude/skills/higgsfield/skills/higgsfield-cmo-agent/starter-packs/coach-course-launch/

Run all 8 stages including the influencer army.
```

The pipeline reads `brief.md` for the coach defaults, captures
your 5-field intake, then runs Stages 1 through 7 with coach-
specific priors applied at each stage.

## What ships

8 files in `~/board/_active/cmo-agent-{{BRAND_SLUG}}-{{YYYY-MM-DD}}/`:

- `00-brief.md` (your captured intake + coach defaults loaded)
- `01-segments.md` (3-5 audience segments, REPEAT + AMPLIFIER flags)
- `02-channel-plan.md` (email + YouTube long-form + organic IG
  primary; LinkedIn / X / Threads secondary by niche)
- `03-creative-briefs.md` (one brief per segment + throughline,
  talking-head + screen-record + walking-and-talking archetypes)
- `04-launch-plan.md` (4-week rollout: 14-day warmup + 7-day cart
  window + 7-day post-close, with REAL kill criteria)
- `05-social-posts.md` (5-8 posts per segment, paste-ready
  Higgsfield prompts for any AI-rendered cuts)
- `06-influencer-army.md` (JV partners + podcast hosts +
  newsletter operators + alumni nano tier with affiliate splits +
  podcast-swap DMs + briefs + kill list)
- `07-higgsfield-prompts.md` (aggregated paste target for the
  Higgsfield UI, typically smaller than DTC packs)

Plus:

- GHL contacts tagged with the campaign + partnership-type sub-tag
- Notion campaign page with DMs ready to copy + send

## Hard rules baked into this pack

- No income claims ("make $10K/mo in 30 days", "first $100K" etc.)
- No rented luxury (Lambo, watch close-up, jet selfie)
- No fake scarcity (only real cohort caps with real dates)
- No DM-bait CTAs in 2026 (use free resource URLs instead)
- No "guru" energy (no Tony Robbins poses, no Miami penthouse
  drone shots)
- No paid testimonials presented as organic
- No "secret sauce" / "unlock" / "elevate" / "transform" vocabulary
- No em dashes, no outcome guarantees, no refund language in copy
