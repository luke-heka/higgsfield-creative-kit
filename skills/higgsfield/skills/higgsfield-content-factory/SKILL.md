---
name: higgsfield-content-factory
description: >
  Use when the user asks to run the Higgsfield Content Factory, build a
  60-day Instagram carousel calendar, auto-generate the next 20 carousels,
  or wants the gated 5-stage research-plan-generate-schedule-cost pipeline.
  This is the Higgsfield-specific carousel production line, it researches
  trending content in the user's niche, plans a 60-day calendar of carousel
  ideas, generates carousels in batches with explicit human gates, optionally
  hands off to Meta MCP for scheduling, then emits a credit-spend vs
  agency-cost report. Hands rendering off to the existing carousel-generator
  and one of the 15 carousel-* templates. Higgsfield only supplies supporting
  imagery for slide 4 / slide 7, slides are NOT rendered by Higgsfield.
  NOT for one-off carousels (use carousel-generator directly for that).
  Trigger phrases: "run the content factory", "build my 60-day carousel
  calendar", "higgsfield content factory pipeline", "auto-generate my next
  20 carousels".
user-invocable: true
metadata:
  tags: [higgsfield, content-factory, carousel, pipeline, instagram, batch, calendar, cost-report]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
---

# Higgsfield Content Factory

## What this is, in plain English

**One-liner:** An assembly line that researches what's working in your niche on Instagram, plans 60 days of carousel posts for you, then builds them 5 at a time with you approving each batch before any AI credits get spent.

**Use it when you want to:**
- Plan 2 months of Instagram carousel posts in one sitting instead of guessing what to post each day.
- Batch-produce 40+ carousels with a checkout-style approval gate so you can stop or change scope between batches.
- See exactly what each batch costs in Higgsfield credits (paid AI image generation) before it runs.
- Get paste-ready captions and slide images dropped into one folder so posting is copy-and-paste, not designing from scratch.

**Don't use it for:**
- A single one-off carousel → use `carousel-generator` plus one of the 15 `carousel-*` template skills.

**Roughly:**
- $9-$24 USD per batch of 5 carousels in Higgsfield credits (only if a batch needs supporting AI images, most batches need zero).
- ~10 minutes of your time per carousel (idea review plus approval clicks). The factory does the rest.
- Output: 40-60 carousels in a dated folder, each with rendered slide PNGs, a paste-ready Instagram caption, and an optional Meta MCP (Facebook's ad-posting tool) handoff to schedule them.

**Inputs you'll need:**
- Your niche in 1-2 sentences (e.g. "AI for solo personal trainers in Australia who run their own gym", NOT "fitness").
- Your brand voice in 1-2 sentences (or defaults to Selr AI house voice).
- A batch size, default 5 carousels per batch.

## Starter packs

Three preconfigured business-owner packs ship with this skill. Pick your industry, fill 3-5 fields, ship a 60-day calendar:

- [`starter-packs/dtc-ecommerce/`](starter-packs/dtc-ecommerce/), Shopify operator 60-day calendar weighted to proof + demos. US English.
- [`starter-packs/personal-trainer/`](starter-packs/personal-trainer/), solo PT + gym owner 60-day calendar weighted to mistakes + tips. AU English.
- [`starter-packs/real-estate-agent/`](starter-packs/real-estate-agent/), solo AU agent 60-day calendar weighted to case-study + suburb cheat-sheets. AU English.

See [`../STARTER-PACKS.md`](../STARTER-PACKS.md) for the full index of 18 packs across all 6 sub-skills.

---

A gated 5-stage IG carousel production pipeline. Built for Selr AI's existing
carousel rendering stack, Higgsfield supplies supporting imagery only, never
the slide itself.

## What This Skill Is (And Is Not)

| This skill IS | This skill is NOT |
|---------------|-------------------|
| The Higgsfield-specific 5-stage carousel pipeline | A general "make me a carousel" trigger |
| A research → calendar → batch generator | A slide renderer (carousel-generator does that) |
| The orchestrator of carousel-generator + 15 templates | A replacement for carousel-generator |
| The bridge that puts Higgsfield images on slide 4/7 only | A path that renders whole slides in Higgsfield |
| A 60-day production calendar builder | A one-off post composer |
| A credit-cost vs agency-cost reporter | A scheduling tool (Meta MCP handoff is optional) |

If the user says "make me a carousel", that's `carousel-generator`. If the
user says "run the content factory" or "build my 60-day calendar", that's
this skill.

---

## When to Invoke

Trigger phrases:

- "run the content factory"
- "build my 60-day carousel calendar"
- "higgsfield content factory pipeline"
- "auto-generate my next 20 carousels"
- "content factory for my niche"
- "batch-generate carousels for the next 2 months"

Do NOT invoke for:

- "Make me a carousel" → `carousel-generator`
- "Build a carousel about X" → `carousel-generator` + a template
- "Pick a carousel template" → template skills themselves
- "Reel" or "video" → motion-graphic-reels / frontcam-reels / notebook-reels
- "Generate an ad" → higgsfield-ugc-ads / selrai-ad-image

---

## The 5 Stages

```
1. RESEARCH  → trending content in user's niche (Apify or fixture)
2. PLAN      → 60-day carousel calendar, idea cards, template assignments
3. GENERATE  → batch-by-batch with explicit human gate before each batch
4. SCHEDULE  → optional Meta MCP handoff for IG scheduling
5. COST      → credit spend vs agency-cost comparison report
```

Each stage is its own prompt file under `prompts/`. The aggregator (this
SKILL.md) routes between them. Each stage MUST be human-gated, no batch
generation without explicit "yes proceed" from the user.

---

## Run Output Location

Every run lands at:

```
~/board/_active/content-factory-<YYYY-MM-DD>/
  ├── 01-research.md
  ├── 02-plan.md
  ├── 03-generate/
  │   ├── batch-01/
  │   │   ├── idea-card.md
  │   │   ├── carousel-template.json
  │   │   ├── higgsfield-prompts.md
  │   │   ├── caption.md
  │   │   └── rendered-slides/  (output from carousel-generator)
  │   ├── batch-02/
  │   └── ...
  ├── 04-schedule.md
  └── 05-cost-report.md
```

NEVER write run output to this skill folder. Always write to `~/board/_active/`.

---

## Dependencies

This skill calls (does NOT re-implement) the following:

### Mandatory

- **`carousel-generator`**, renders all slides via Puppeteer + Manrope. Skill
  passes it a `template.json`; carousel-generator returns PNGs. NEVER use
  Higgsfield to render a whole slide.
- **One of 15 carousel templates** (pick by post-type, see template selection
  table below):
  - `carousel-tips`
  - `carousel-cheat-sheet`
  - `carousel-stack-reveal`
  - `carousel-case-study`
  - `carousel-myth-bust`
  - `carousel-mistakes`
  - `carousel-feature-update`
  - `carousel-feature-spotlight`
  - `carousel-skill-announce`
  - `carousel-skill-card`
  - `carousel-metaphor-explainer`
  - `carousel-prompt-anatomy`
  - `carousel-replace-this`
  - `carousel-reel-cover` (only for reel-cover post-types)
- **`alex-hormozi-content-method`**, structure spine (hook + 5 tips + CTA).
  Loaded into every idea-card.
- **`content-engine`**, voice grade + slop check. MANDATORY ship-gate before
  saving ANY text file in any stage.
- **`humanizer`**, final AI-tell removal. MANDATORY ship-gate after
  content-engine, before saving.

### Optional

- **`apify-content-analytics`**, Stage 1 research data source (IG, FB, YT,
  TikTok trending). If MCP not available, fall back to
  `examples/sample-trending-fixture.json`.
- **`community-drop`** skill (wraps the community-publishing-pipeline
  workflow), Stage 3 slide-7 CTA handoff to ManyChat. Use when the
  carousel has a "Comment WORD" CTA.

### Shared assets (read, do NOT duplicate)

- `../shared/higgsfield-prompt-skeletons.md`, Skeleton 3 for slide 4 / slide
  7 supporting imagery. NEVER use Skeleton 3 for whole-slide rendering.
- `../shared/hook-bank-100.md`, 100 hook archetypes. Used in Stage 2 to seed
  idea cards.
- `../shared/element-tagging.md`, `@product` tag convention if the carousel
  features a recurring product image across slides.

---

## Template Selection (post-type → template)

Stage 2 picks the carousel template per idea card from this table. Stage 3
follows the assignment without re-deciding.

| Post-type / intent | Template |
|--------------------|----------|
| 5 tips / 7 tips / N tips | `carousel-tips` |
| Cheat sheet / reference card | `carousel-cheat-sheet` |
| Tool stack reveal / "here's what I use" | `carousel-stack-reveal` |
| Case study with numbers | `carousel-case-study` |
| Myth busting / "X is wrong" | `carousel-myth-bust` |
| Common mistakes / "stop doing X" | `carousel-mistakes` |
| Feature launch announcement | `carousel-feature-update` |
| Single feature deep-dive | `carousel-feature-spotlight` |
| New skill / module announce | `carousel-skill-announce` |
| Skill card / capability card | `carousel-skill-card` |
| Metaphor / analogy explainer | `carousel-metaphor-explainer` |
| Prompt anatomy / XML walkthrough | `carousel-prompt-anatomy` |
| Before/after replacement | `carousel-replace-this` |
| Reel cover (single image) | `carousel-reel-cover` |

If no entry matches, default to `carousel-tips`.

---

## Voice Ship-Gate (MANDATORY)

Before saving ANY text file produced by ANY stage:

1. Pipe the text through `content-engine` (voice grade + slop check).
2. Pipe the output through `humanizer` (AI-tell removal).
3. Only then write to disk.

Documented again in every stage prompt. If content-engine returns a "fix"
verdict, do NOT save, re-write and re-grade. Loop until pass.

---

## Style Constraints (Selr AI House Style)

These apply to every text file produced by this skill (hooks, body, captions,
CTAs):

- **No em dashes.** Use commas or full stops.
- **Banned vocab:** "game-changer", "10x", "crushing it", "killing it",
  "secret sauce", "level up", "unlock", "transform", "revolutionary",
  "elevate", "leverage", "dive deep", "delve into", "in today's fast-paced
  world", "the power of".
- **No outcome guarantees.** No "you will get X". Use process language ("here
  is how we built it", "the steps we walked through").
- **No support promises.** No "weekly Q&A", "ongoing help", "support included
  forever".
- **No drop-in invites.** No "come say hi", "swing past", "drop in if
  you're nearby".
- **No refund / money-back / satisfaction guarantees.**
- **AU English.** "Optimise" not "optimize", "colour" not "color".
- **No the founder's personal life** in marketing copy.

---

## The Workflow (Top-Down)

### Pre-flight check

Before invoking any stage, confirm:

1. Higgsfield MCP available? Run `ToolSearch` query `higgsfield`. If not
   connected, route the user to `higgsfield-connector` first, then resume.
2. Output folder exists? Create `~/board/_active/content-factory-<TODAY>/`.
3. User has provided: niche, brand handle, brand voice notes (if not Selr
   AI default).

### Confirm before building (token + credit discipline)

This pattern is non-negotiable. Before any expensive stage (Plan, Generate),
restate to the user:

```
Here is what I'm about to do:
- Stage: <STAGE NAME>
- Inputs: <NICHE>, <BRAND>, <BATCH SIZE>
- Expected output: <FILES> at <PATH>
- Expected credit spend: <ESTIMATE>

Proceed? (yes / adjust / cancel)
```

If the user says "adjust", refine and re-confirm. Never proceed silently.

### Stage 1: Research

Run `prompts/01-research.md`. Inputs: niche, brand voice. Output:
`01-research.md` with trending posts table, competitor handles, hook
patterns, top 20 idea candidates.

Data source: `apify-content-analytics` MCP if available. Falls back to
`examples/sample-trending-fixture.json` if blocked / not connected. NEVER
fabricate trends, flag fixture mode at the top of `01-research.md` if used.

### Stage 2: Plan

Run `prompts/02-plan.md`. Inputs: research output, batch cadence (default:
5 carousels / week = ~40 over 60 days). Output: `02-plan.md` containing
the 60-day calendar (date → carousel idea → template → batch number),
plus full idea cards (one per row) following `templates/idea-card.md`.

### Stage 3: Generate (batched + human-gated)

Run `prompts/03-generate.md` ONCE PER BATCH. Default batch size: 5
carousels. NEVER auto-advance to the next batch without explicit "yes
proceed" from the user.

Per carousel within a batch:

1. Read the idea card from Stage 2.
2. Look up template assignment.
3. Build `carousel-template.json` (slide-by-slide content matching the
   template's schema). Voice-grade every text field via content-engine +
   humanizer.
4. If slide 4 or slide 7 needs a supporting image, build a Higgsfield image
   prompt using Skeleton 3 from `../shared/higgsfield-prompt-skeletons.md`.
   Call Higgsfield MCP (ToolSearch query `higgsfield`, pick image tool).
   Save the image. Reference it in the carousel-template.json.
5. Build the caption using `templates/caption-template.md`. Voice-grade.
6. Hand `carousel-template.json` to `carousel-generator`. Render PNGs.
7. Write everything to `03-generate/batch-NN/<carousel-slug>/`.

After each batch: report what was rendered, total credits spent so far,
ask the user to proceed to next batch or stop.

### Stage 4: Schedule (optional)

Run `prompts/04-schedule.md`. Only invoked if user explicitly asks for
scheduling. Hands off to Meta MCP for IG (or `omnisocials` for multi-
platform). If neither available, writes a `04-schedule.md` with paste-ready
captions + slide paths the user can manually schedule.

If carousels have a "Comment WORD" CTA, also runs the `community-drop`
skill (wraps the community-publishing-pipeline workflow) to wire up the
ManyChat trigger.

### Stage 5: Cost Report

Run `prompts/05-cost-report.md`. Pulls Higgsfield credit spend, multiplies
by Higgsfield credit cost in USD, compares against (a) typical agency
production cost for the same volume, (b) freelancer cost. Output:
`05-cost-report.md`, readable receipt suitable for client sell or internal
ROI doc.

---

## Routing Constraints (Avoid Trigger Collision)

This skill must NOT be invoked when the user is asking for:

- A single carousel → `carousel-generator`
- Choosing a carousel template → individual template skills
- A reel or video → `motion-graphic-reels` / `frontcam-reels` / `notebook-reels`
- A static ad image → `selrai-ad-image`
- A UGC video ad → `higgsfield-ugc-ads`
- A one-prompt campaign → `higgsfield-marketing-studio`
- Deconstructing a viral post → `higgsfield-viral-replicator`

The trigger surface of this skill is narrowly the multi-stage carousel
factory. Do not poach broader content triggers.

---

## Per-Stage Kill Criteria

If any of these conditions hit at any stage, STOP and ask the user before
continuing:

- Niche is too broad ("entrepreneurs", "business owners"), ask for a 1-2
  sentence ICP.
- Research returned <5 viable trending posts, ask the user to narrow the
  niche or supply manual references.
- Plan produced <20 distinct idea cards for a 60-day calendar, flag and
  ask whether to extend research or accept a shorter calendar.
- Any text passes through content-engine 3 times with "fail" verdict ,
  STOP. Ask the user to rewrite manually. Do not ship slop.
- Batch generation costs are tracking >2x the pre-flight estimate, STOP.
  Ask the user to adjust scope.

---

## Field-by-Field Discipline

Every prompt under `prompts/` and every template under `templates/` follows
Hewitt's convention:

- Numbered field-by-field skeleton.
- One worked example per skeleton.
- "Rejected" section showing patterns to avoid.
- Kill criteria, when to stop and ask.

The carousel slide image prompt (Skeleton 3 from
`../shared/higgsfield-prompt-skeletons.md`) is the canonical reference for
slide 4 / slide 7 supporting imagery. Do NOT duplicate it here.

---

## Confirm-Before-Building Examples

Stage 2 confirmation:

```
About to plan a 60-day carousel calendar.
- Niche: "AI for solo personal trainers" (your ICP)
- Cadence: 5 carousels / week = 40 ideas
- Templates: will pick from the 15 available per idea
- Output: ~/board/_active/content-factory-2026-05-24/02-plan.md
- No Higgsfield credit spend at this stage (planning only).

Proceed? (yes / adjust niche / cancel)
```

Stage 3 batch confirmation:

```
About to generate batch 02 of 08 (5 carousels).
- Templates: carousel-tips, carousel-myth-bust, carousel-cheat-sheet,
  carousel-tips, carousel-case-study
- Higgsfield supporting images: 3 (slide 4 of carousel #2, #4, #5)
- Expected credit spend: ~150 credits (~$9 USD)
- Running total after this batch: ~$18 USD vs estimated batch budget $24

Proceed? (yes / skip this batch / pause)
```

---

## When MCP Is Not Connected

Every stage has a graceful fallback:

| Stage | If MCP missing | Fallback |
|-------|----------------|----------|
| 1. Research | apify-content-analytics down | Use `examples/sample-trending-fixture.json`, flag fixture mode |
| 3. Generate (Higgsfield image) | Higgsfield MCP down | Write paste-ready image prompt to `higgsfield-prompts.md`, user runs manually |
| 3. Generate (carousel-generator) | carousel-generator missing | Hard-stop, install carousel-generator first |
| 4. Schedule | Meta MCP / omnisocials down | Write paste-ready captions + slide paths to `04-schedule.md` |

Never invent data. If a fallback fires, flag it at the top of the run
folder's README.md.

---

## Pairs With

- **Jason Lee daily-carousel routine** (YouTube `WvuLxxDY37U`), this skill
  is the formalisation of his "skill-as-orchestrator + routine" pattern,
  with Selr AI's voice + render stack swapped in.
- **Higgsfield Content Factory** (YouTube `l7W3QzU8w5s`), the 5-stage shape
  comes from the official Higgsfield walkthrough. Adapted for carousels
  (their version was UGC video).

---

## Files in This Skill

```
higgsfield-content-factory/
├── SKILL.md                          (this file)
├── prompts/
│   ├── 01-research.md                Stage 1: research trending in user's niche
│   ├── 02-plan.md                    Stage 2: 60-day calendar, idea cards
│   ├── 03-generate.md                Stage 3: per-carousel build w/ human gates
│   ├── 04-schedule.md                Stage 4: optional Meta MCP / IG handoff
│   └── 05-cost-report.md             Stage 5: credit spend vs agency cost
├── templates/
│   ├── idea-card.md                  Idea card schema (one row of the plan)
│   └── caption-template.md           IG caption shape
└── examples/
    └── sample-trending-fixture.json  Deterministic fallback for research
```

---

## Related Skills

- `carousel-generator`, slide rendering engine (this skill calls it)
- 15 `carousel-*` template skills, slide design layer (this skill picks
  from them per idea card)
- `alex-hormozi-content-method`, content structure spine
- `content-engine`, voice ship-gate
- `humanizer`, AI-tell removal
- `apify-content-analytics`, Stage 1 research source
- `community-drop`, Stage 3/4 ManyChat CTA wiring (wraps the community-publishing-pipeline workflow)
- `higgsfield-connector`, MCP setup if not connected
- `higgsfield-vibe-motion`, for motion graphics (different skill)
- `higgsfield-ugc-ads`, for UGC video ads (different skill)
- `motion-graphic-reels`, for reels (different skill)
- `frontcam-reels` / `notebook-reels`, talking-head and notebook-style reels (different skills)
