# DTC Product Drop Starter Pack

A preconfigured starter pack for `higgsfield-cmo-agent`. Use this when
you're launching a physical DTC product (skincare, supplement, apparel,
drinkware, home goods) and want the 8-stage campaign pipeline pre-tuned
for DTC voice, visuals, and channel mix.

## What you get

- `brief.md`, preset Stage 0 intake. DTC voice rules, ban-list,
  channel defaults (Meta + TikTok primary), visual archetypes
  (phone-shot, real homes, no studio look).
- `prompts.md`, three paste-ready prompts: kickoff for Stage 0 to
  Stage 1, DTC creative brief variant for Stage 3, DTC influencer
  DM variant for Stage 6.
- `sample/`, placeholder for an example campaign run.

## When to use this pack

- You're launching a physical DTC product priced $25 to $120 AOV.
- The brand sells direct-to-consumer through its own store, TikTok
  Shop, or both.
- The campaign goal is launch + awareness, building a retargeting
  audience, and seeding the repurchase ladder.
- US English by default. Override to AU or UK at Stage 0 intake if
  the brand sells locally only.

Don't use this pack if the brand is B2B SaaS, a coach or course
creator (see `coach-course-launch` pack), or a local service business
(see `local-service-opening` pack).

## The 5-field brief

To run a full campaign, you need:

1. **Brand name** (e.g. "Coastal Skin Co")
2. **Hero product or SKU** being dropped (e.g. "The Daily Serum")
3. **Price** + AOV threshold (e.g. "$48, free shipping over $75")
4. **Launch date** in ISO format (e.g. "2026-06-12")
5. **Hero benefit**, the one specific observable outcome the
   product produces (e.g. "absorbs in 8 seconds, no white cast")

Optional but useful: founder name, incumbent competitor the
customer is switching from, ingredient or mechanism, target concern,
existing UGC library status.

## Cost

- **Documents only:** ~$0. The pipeline produces 8 markdown files,
  paste-ready Higgsfield prompts, and a Notion campaign page. No
  paid renders.
- **With renders:** $5 to $40 per campaign depending on how many
  Higgsfield previews you opt into. Each video preview is ~$1 to
  $3 of Higgsfield credit, each image preview ~$0.20 to $0.50.

## Time

- **Per full 8-stage run:** 15 to 25 minutes. Each stage saves to
  disk, you review, then the next stage dispatches.
- **First-time setup:** add ~5 minutes for capturing the brief and
  reviewing the DTC-vertical priors.

## How to run

```text
Build me a complete multi-channel marketing campaign for the
{{BRAND}} {{OFFER}} drop on {{LAUNCH_DATE}}. Use the DTC product
drop starter pack at
~/.claude/skills/higgsfield/skills/higgsfield-cmo-agent/starter-packs/dtc-product-drop/

Run all 8 stages including the influencer army.
```

The pipeline reads `brief.md` for the DTC defaults, captures your
5-field intake, then runs Stages 1 through 7 with DTC-specific
priors applied at each stage.

## What ships

8 files in `~/board/_active/cmo-agent-{{BRAND_SLUG}}-{{YYYY-MM-DD}}/`:

- `00-brief.md` (your captured intake + DTC defaults loaded)
- `01-segments.md` (3-5 audience segments, REPEAT + AMPLIFIER flags)
- `02-channel-plan.md` (Meta + TikTok primary, email + IG secondary)
- `03-creative-briefs.md` (one brief per segment + throughline)
- `04-launch-plan.md` (4-week rollout ending ~3 weeks post-drop)
- `05-social-posts.md` (5-8 posts per segment, paste-ready Higgsfield
  prompts for video and still posts)
- `06-influencer-army.md` (micro + nano tiers with DTC-specific DMs +
  briefs + creator codes + repost-rights asks)
- `07-higgsfield-prompts.md` (aggregated paste target for the
  Higgsfield UI)

Plus:

- GHL contacts tagged with the campaign + tier sub-tag
- Notion campaign page with DMs ready to copy + send

## Hard rules baked into this pack

- No medical claims for supps or skincare
- No "shop now" end-cards
- No studio-set / cinema-lit visuals
- No stock B-roll or stock music beds
- No celebrity look-alikes or AI-generated faces in product hero shots
- No before/after photos with altered lighting or filters
- No paid testimonials presented as organic
- No em dashes, no outcome guarantees, no refund language in copy
