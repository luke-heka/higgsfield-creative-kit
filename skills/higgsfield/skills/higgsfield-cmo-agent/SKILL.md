---
name: higgsfield-cmo-agent
description: >
  Use when the user wants a complete multi-channel marketing campaign produced
  in one pass from a brand brief, audience segments with REPEAT/AMPLIFIER
  flags, per-segment channel plan, creative briefs, 4-week launch plan with
  kill criteria, 5-8 social posts per segment each with a paste-ready
  Higgsfield prompt, a tiered influencer army with personalised DMs, and an
  aggregated Higgsfield-prompts file that's the literal paste target for the
  Higgsfield UI. Eight-stage gated pipeline (00-brief → 07-aggregator).
  Selr AI brand defaults auto-load from selrai-business-model.md +
  brand-contact-urls.md when the user says "for Selr AI", skipping the intake
  interview. Carousel-shaped posts hand off to carousel-generator (not
  Higgsfield slide rendering). Influencer handles write to GHL as tagged
  contacts and a Notion page. CTAs wire through the community-drop skill.
  Every stage pipes through content-engine + humanizer as a mandatory voice
  ship-gate. Trigger phrases: "build a marketing campaign for [brand]",
  "describe the ideal customer for [product]", "give me an influencer army
  for [brand]", "complete multi-channel campaign", "higgsfield CMO agent",
  "full campaign, segments, briefs, posts, influencers", "channel plan +
  influencer plan for [brand]". Does NOT poach content-marketer (persona-only)
  or marketing-agency (top-level brain). This is the Higgsfield-specific
  campaign orchestrator that emits paste-ready Higgsfield prompts.
user-invocable: true
metadata:
  tags: [higgsfield, cmo-agent, campaign, marketing, segments, channel-plan, creative-brief, launch-plan, social-posts, influencer-army, multi-channel, orchestrator, gated-pipeline]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
---

# Higgsfield CMO Agent

## What this is, in plain English

**One-liner:** Give it a brand brief (or just say "for Selr AI"), and it builds a full marketing campaign for you in eight steps: audience segments (the types of customers you're targeting), a channel plan (where you'll reach them), creative briefs (what to actually say), a 4-week launch timeline, 5-8 ready-to-post social posts per segment, a tiered influencer outreach list with personalised DMs already drafted, plus all the Higgsfield image and video prompts you'd need to actually shoot it.

**Use it when you want to:**
- Plan a marketing campaign for a new product launch from scratch, without spending two weeks figuring out where to start
- Rebuild a stalled brand or repositioning effort with fresh segments and a real channel plan
- Figure out which platforms to focus on for a specific product, and what each post should look like
- Produce all the social posts, influencer outreach, and creative briefs for a 4-week launch in one sitting, ready to hand off or ship

**Don't use it for:**
- One-off Instagram carousels with no campaign behind them (use `carousel-generator`, or `higgsfield-content-factory` for a 60-day carousel calendar)
- Single ad creative variations or UGC-style ad scripts (use `higgsfield-ugc-ads` or `ad-creative`)
- Pure copywriting jobs (page copy, headlines, emails) without campaign strategy underneath (use `copywriting`, `direct-response-copy`, or `email-content-engine`)

**Roughly:**
- Cost: usually $0 unless you opt in to render Higgsfield previews on top (the skill primarily produces documents and paste-ready prompts, not rendered media)
- Time: 15-25 minutes for a 4-segment campaign with 6 posts per segment and 2 influencer tiers, with you approving each stage before it moves on
- What you get: 8 numbered documents in a dated folder, plus a single aggregated paste-target file of every Higgsfield prompt, plus your influencer outreach list written to GHL as tagged contacts AND a Notion campaign page with the DMs already drafted for you to review and send manually

**Inputs you'll need:**
- A brand brief OR just say "for Selr AI" (it auto-loads Selr AI brand defaults from memory, skipping the interview)
- A campaign goal: awareness / launch / repositioning / retention (or for Selr AI runs: workshop registrations / Skool conversions / ASA pipeline)
- Optional: tone or visual reference brands, a target city or date window, and any hard exclusions (visuals you don't want, claims you won't make, channels you won't run)

## Starter packs

Three preconfigured business-owner packs ship with this skill. Each is a full 8-stage launch:

- [`starter-packs/dtc-product-drop/`](starter-packs/dtc-product-drop/), DTC product drop + awareness launch. Meta + TikTok primary.
- [`starter-packs/coach-course-launch/`](starter-packs/coach-course-launch/), course launch with cart open/close. Email + organic IG + long-form YouTube. No income claims.
- [`starter-packs/local-service-opening/`](starter-packs/local-service-opening/), grand opening for a local trade or hospo business. TikTok Local Feed + Google Business. AU.

See [`../STARTER-PACKS.md`](../STARTER-PACKS.md) for the full index of 18 packs.

---

Take a brand brief and produce a launch-ready multi-channel marketing campaign
in one pass: who you're selling to, where you'll reach them, what the creative
says, when each asset ships, what the posts look like, which influencers to
enlist, and a single aggregated file of Higgsfield prompts you can paste
straight into the Higgsfield UI.

Eight-stage gated pipeline. Each stage writes a numbered file. The eighth
stage is the aggregator, the demo paste target.

This skill assumes the **Higgsfield MCP** is connected (set up via
`higgsfield-connector`). If it is, the skill calls Higgsfield directly to
render hero visuals where the user wants previews. If it isn't, every visual
is delivered as a paste-ready Higgsfield prompt and the run still completes.

---

## What This Skill Is (And Is Not)

| This skill IS | This skill is NOT |
|---------------|-------------------|
| The Higgsfield-specific multi-channel campaign orchestrator | A persona ("act as my CMO"), that's `content-marketer` |
| Eight gated stages with one file per stage | A single-shot prompt → asset call |
| Outputs paste-ready Higgsfield prompts per post | A Higgsfield renderer (it can call the MCP but doesn't need to) |
| Wires influencer handles to GHL + Notion + ManyChat | A standalone CRM tool, uses the existing `ghl-crm` + `Notion:create-page` + `community-drop` skills |
| Auto-loads Selr AI brand defaults when brand="Selr AI" | A generic CMO brain, it's Higgsfield-stack-specific |
| Mandatory voice ship-gate via `content-engine` + `humanizer` | A one-pass copy generator, every stage's copy gets graded |
| Carousel posts hand off to `carousel-generator` | A Higgsfield-rendered-slide carousel maker (Selr brand uses Remotion + Fraunces) |
| AU English in Selr-defaulted runs (colour, optimise, specialise) | US English by default, it picks based on the brand |

If the user says "build me a campaign for Selr AI" → this skill, defaults loaded.
If the user says "act as my CMO and review this strategy" → `content-marketer`.
If the user says "render me one Higgsfield clip" → `higgsfield-marketing-studio`.
If the user says "make me a 7-slide carousel" → `higgsfield-content-factory` +
`carousel-generator`.

---

## When to Invoke

Trigger phrases (description routes on these, keep them sharp):

- "build a marketing campaign for [brand]"
- "build me a marketing campaign"
- "complete multi-channel campaign for [brand]"
- "describe the ideal customer for [product]"
- "give me an influencer army for [brand]"
- "higgsfield CMO agent"
- "channel plan + influencer plan for [brand]"
- "full campaign, segments, briefs, posts, influencers"
- "audience segments and channel plan for [brand]"

Do NOT invoke for:

- "act as my CMO and review X" → `content-marketer`
- "make me a 7-slide carousel" → `higgsfield-content-factory`
- "render one Higgsfield clip" → `higgsfield-marketing-studio`
- "write ad headlines for X" → `ad-creative`
- "write me an email sequence" → `email-content-engine`

---

## Brand Default Auto-Load (Selr AI Shortcut)

If the user says any of:

- "for Selr AI"
- "for Selr"
- "use the Selr AI defaults"
- "Selr AI workshop campaign"
- "my brand"

**Skip the intake interview entirely.** Auto-load brand context from:

1. `~/.claude/projects/-Users-luke/memory/selrai-business-model.md` (V4.1.2)
   - Hero offers: In-person Workshop $1,500 AUD, Online Standard $499 AUD,
     Skool Premium $499/mo USD (3-mo lock-in), AI Systems Architecture from
     $5K AUD, High-end Consulting (scoped), Strategy Call $1,500 AUD.
   - Positioning: hands-on AI rollout for AU SMB operators.
   - Voice: confident, direct, AU English, no hype.
   - Bans: see "Extended Ban-List" below.
2. `~/.claude/projects/-Users-luke/memory/brand-contact-urls.md`
   - IG: @selr__ai (double underscore) + @mr_heka
   - YouTube: @mr_heka
   - Workshop landing: workshop.selrai.com.au
   - Short-link domain: link.selrai.com.au (for booking/payment, never in footers)
3. ICP defaults for Selr AI workshop campaigns:
   - AU SMB operators (5-50 staff), trades, hospitality, professional services
   - Solo founders building agencies / consultancies on AI
   - Mid-career operators repositioning into AI roles
4. Campaign goal default: drive registrations for the next workshop city.

Write the loaded defaults to `00-brief.md` so the user can see what got
pulled. The user can override any field by replying inline.

For non-Selr brands, run the full intake interview in Stage 0.

---

## Output Destination

Runs write to:

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/
```

Where `<brand-slug>` is `selr-ai` for default runs, or a kebab-case slug from
the brand name otherwise.

Files inside:

```
00-brief.md
01-segments.md
02-channel-plan.md
03-creative-briefs.md
04-launch-plan.md
05-social-posts.md
06-influencer-army.md
07-higgsfield-prompts.md   ← THE PASTE TARGET
```

The user can read sequentially or jump to any stage. Stage 7 is the
aggregator, every Higgsfield prompt from Stages 5 and 6 reformatted into a
single clean file the user pastes into the Higgsfield UI on camera.

---

## Workflow: Run in Order, One File per Stage

Create the output directory first:

```bash
mkdir -p ~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>
```

Then walk these stages, loading each prompt fragment from `prompts/` and
writing the output:

| # | Prompt fragment | Output file | Voice gate? |
|---|-----------------|-------------|-------------|
| 0 | `prompts/00-brief.md` | `00-brief.md`, captured intake OR auto-loaded Selr AI defaults | No (factual capture) |
| 1 | `prompts/01-segments.md` | `01-segments.md`, 3-5 segments with REPEAT/AMPLIFIER/NEITHER flags + rejected footer | Yes |
| 2 | `prompts/02-channel-plan.md` | `02-channel-plan.md`, per-segment channel table + cross-segment leverage | Yes |
| 3 | `prompts/03-creative-brief.md` | `03-creative-briefs.md`, one brief per segment + throughline | Yes |
| 4 | `prompts/04-launch-plan.md` | `04-launch-plan.md`, 4-week rollout with kill criteria | Yes |
| 5 | `prompts/05-social-posts.md` | `05-social-posts.md`, 5-8 posts per segment with caption + Higgsfield prompt + why-it-works | Yes |
| 6 | `prompts/06-influencer-army.md` | `06-influencer-army.md`, tiered table + personalised DMs + per-influencer briefs + kill list | Yes |
| 7 | `prompts/07-higgsfield-prompts.md` | `07-higgsfield-prompts.md`, AGGREGATED Higgsfield prompts from Stages 5+6 | No (reformat only) |

The user can run stages sequentially or jump to any stage. If they jump
mid-pipeline, surface a warning that downstream stages need upstream context
and offer to re-run from Stage 0.

---

## Voice Ship-Gate (Mandatory: Every Copy Output)

Every copy stage (1-6) pipes through this gate before saving:

1. **Draft**, Generate the stage output per the prompt fragment.
2. **Grade via `content-engine`**, 5-axis critic checks for slop, hype,
   support promises, outcome guarantees, drop-in invites, personal life in
   marketing, em dashes, AU/US English mismatch (for Selr runs, must be AU).
3. **Hard-fail rewrite**, If any axis fails, rewrite the offending lines
   and re-grade. Do not save a failing draft.
4. **Humaniser pass**, Run through `humanizer` skill to strip Wikipedia
   signs-of-AI-writing patterns (inflated symbolism, promotional adjectives,
   superficial -ing analyses, vague attributions, rule-of-three overuse,
   AI vocabulary, negative parallelisms, excessive conjunctive phrases).
5. **Save final**, Write to the stage file only after both gates pass.

The Stage 7 aggregator does NOT need voice grading, it's a mechanical
reformat of already-graded prompts from Stages 5 and 6.

---

## Extended Ban-List (Selr AI House Style)

In addition to Hewitt's base bans (no "crushing it", no "killing it", no
"game-changer", no "10x", no "secret sauce"), Selr AI runs add:

- **No support promises**, "we'll always be here", "weekly Q&A", "ongoing
  helpdesk", "any time you need us". Business-survival rule.
- **No outcome guarantees**, "you'll grow X% in Y weeks", "guaranteed
  results", "we promise you'll close N deals". Use process language ("hands-on
  install", "walk through together") not outcome ("system will be running
  before you leave").
- **No drop-in invites**, "come say hi", "swing past", "stop by", "if
  you're nearby", "come hang out". Every unpaid chat displaces a $1,500
  scoping call.
- **No personal life**, "my family", "my kids", "my wife", "my house",
  "my morning routine". Luke's personal life is off-limits for marketing.
  Hard firewall.
- **No refund promises**, no "money-back guarantee", "30-day refund",
  "if you don't love it, we'll refund". Refunds attract cheeky buyers who
  game the offer.
- **No em dashes**, use commas, full stops, or rewrite. Replace any
  em-dash in Hewitt's seed prompts before saving.
- **AU English in Selr runs**, colour, optimise, specialise, organisation,
  realised, metre, kilometre.

The full canonical ban-list lives in `content-engine` skill. This is the
copy-fast reference. When in doubt, run the gate.

---

## Higgsfield Handoff Per Post

For every visual asset across Stages 5-6:

1. **Compose the prompt** using `templates/higgsfield-image-prompt.md` or
   `templates/higgsfield-video-prompt.md`. Both reference the canonical
   shared skeletons at `../shared/higgsfield-prompt-skeletons.md` (Skeletons
   1 and 2).
2. **Inject element tags** where multi-chunk consistency matters. Reference
   `../shared/element-tagging.md` for `@product` / `@logo` / `@founder`
   patterns.
3. **Open the post-shape decision tree:**
   - If post format is "IG carousel" → DO NOT render slides via Higgsfield
     for Selr brand. Hand off to `carousel-generator` (Remotion + Fraunces
     hand-typeset). Higgsfield only supplies background imagery for slide 4
     or slide 7 if requested.
   - If post format is "9:16 video / Reel / TikTok" → write Higgsfield video
     prompt (5-8s, ONE action).
   - If post format is "static still / 4:5 IG / 1:1" → write Higgsfield
     image prompt.
   - If post format is "X / LinkedIn text post" → no Higgsfield prompt
     needed, copy only.
4. **MCP-render gate (optional preview):** If the user wants previews
   rendered now, call `ToolSearch` with query `higgsfield` to discover the
   current tool names. Use the matched tool that fits the asset type (image
   vs video). Never invent Higgsfield tool names, always discover at
   runtime via ToolSearch.
5. **No MCP-render = paste-ready only:** If the MCP isn't connected or the
   user wants prompts only, save the prompt and tell the user to paste it
   into the Higgsfield web UI (link to `higgsfield.ai`).

---

## Skill Dependencies (Call During Run)

This skill orchestrates a chain of existing skills. None of them get
re-implemented here, we call them.

| Skill | When called | What it does for this skill |
|-------|-------------|------------------------------|
| `content-engine` | Stages 1-6 (mandatory voice gate) | Voice filter + slop blocklist + 5-axis critic |
| `humanizer` | Stages 1-6 (mandatory slop gate) | Wikipedia signs-of-AI-writing detector + rewriter |
| `direct-response-copy` | Stage 5 (DR-style post captions) | DR copy generation for hook-driven captions |
| `copywriting` | Stage 4 (if launch plan includes landing/page copy rows) | Landing/page/hero/CTA copy |
| `ad-creative` | Stage 5 (paid amplification posts in the hero 3) | Headline + primary text variants for paid channel runs |
| `email-content-engine` | Stage 2 (when email is a chosen channel) | Email channel handoff for sequences/broadcasts |
| `content-marketer` | Stage 3 (elite strategist persona for creative direction) | Elite-CMO-grade strategic phrasing for the brief |
| `alex-hormozi-content-method` | Stages 4-5 (volume + structure) | Volume framework, give-give-give-ask, 3P opener |
| `social-content` | Stage 5 (organic platform routing for each post) | Per-platform format and posting-time guidance |
| `carousel-generator` | Stage 5 (carousel-shaped posts) | Render Selr-brand carousels via Remotion + Fraunces |
| `ghl-crm` | Stage 6 (post-aggregation) | Write chosen influencer handles to GHL as tagged contacts |
| `Notion:create-page` | Stage 6 (post-aggregation) | Write influencer briefs to a Notion campaign page |
| `community-drop` | Stage 5 + Stage 7 (CTA wiring) | Wire CTAs through GitHub → Notion → ManyChat for community drops. Reference pattern: `~/.claude/projects/-Users-luke/memory/community-publishing-pipeline.md` |

For any skill not yet connected, surface the gap to the user and offer to
install via the matching `*-mcp-setup` skill. Do not silently fall through.

---

## Stage-by-Stage Detail

### Stage 0: Brief Capture (`prompts/00-brief.md`)

**Goal:** Get every input needed to run Stages 1-7 without further
interruption.

**Two paths:**

- **Selr AI auto-load** (user said "for Selr AI" / "for Selr" / etc.):
  Skip the interview. Load defaults from
  `selrai-business-model.md` + `brand-contact-urls.md`. Capture only:
  - Which offer (workshop / Skool / ASA / consulting / strategy call)
  - Which city (if workshop)
  - Campaign goal (registrations / Skool conversions / ASA pipeline)
  - Date window
- **Generic intake interview** (any other brand): one batched ask covering:
  1. Brand name (or "skip, invent one")
  2. Hero product + price band
  3. One-line positioning
  4. Best guess at ICPs (1-3)
  5. Campaign goal: awareness / launch / repositioning / retention
  6. Tone/visual references (URLs or "no opinion")
  7. AU or US English
  8. Hard exclusions (visuals, channels, claims, language)

Write to `00-brief.md` in the format from `templates/segment-card.md`'s
brief block. This is the source of truth for Stages 1-7, every later stage
re-reads this file.

### Stage 1: Audience Segments (`prompts/01-segments.md`)

**Goal:** 3-5 audience segments with the canonical Hewitt structure, with
Selr-style flags.

**Rules:**

- If the brief includes ICP guesses, validate or rewrite. Do not just
  restate.
- Reject any segment that's a lifestyle aesthetic without a specific
  job-to-be-done.
- Flag ONE segment as REPEAT (most-likely repeat buyer / member /
  re-purchaser).
- Flag ONE segment as AMPLIFIER (most-likely word-of-mouth driver).
- If two segments overlap >70%, merge.

**Per-segment fields:** Demographic, Psychographic, Job-to-be-done (one
functional + one emotional), Where they live online (specific surfaces, not
"outdoor content"), Where they live offline, Buying trigger, Why this brand
wins for them, Repeat/Amplifier flag.

**Footer (mandatory):** "Segments we considered and rejected", one
paragraph naming the cuts so the user sees the thinking, not just the
output.

**Voice gate:** Run through `content-engine` + `humanizer` before saving.

### Stage 2: Channel Plan (`prompts/02-channel-plan.md`)

**Goal:** Per-segment channel mix with cadence honest enough that a 1-2
person team can ship it.

**Rules:**

- Max 2 primary channels per segment. If a third can't be justified, don't
  add it.
- Every channel needs a content format ("YouTube long-form how-to" not
  "YouTube").
- Cadence honest, what can actually ship weekly without burning the team.
- One table per segment.

**Per-segment table columns:** Role (Primary / Secondary / Amplifier),
Channel, Format, Cadence, Why this fits.

**Amplifier row:** This is where influencer / UGC / community plays land.
Keep concrete, not aspirational.

**Footer (mandatory):** Cross-segment leverage, 4-6 lines naming which
formats can be cut once and re-used across segments (e.g. one hero film →
3 segment-specific 15s edits).

**Voice gate:** Yes.

### Stage 3: Creative Briefs (`prompts/03-creative-brief.md`)

**Goal:** One brief per segment. These drive every post in Stage 5 and every
influencer angle in Stage 6. Written so the next person to read them is the
photographer / director.

**Per-segment brief fields:**

- Big idea (one sentence, no commas)
- Insight we're leveraging (one paragraph customer truth)
- Message hierarchy (Lead with / Support with / Demonstrate by showing /
  Permission to believe)
- Visual direction (Setting / Subject(s) / Lighting / Camera energy / Color
  palette anchors / Texture cues / Product visibility)
- Voice/copy direction (Tone words 3 max / Phrases to use / Phrases banned ,
  Selr ban-list applies)
- Do (3-5 things creative MUST do)
- Don't (3-5 things creative MUST NOT do, visual cliches, hype words, etc.)
- Reference clues (2-3 short text descriptions, NOT a moodboard, NOT brand
  names, describe by composition)

**Footer (mandatory):** "The throughline", one paragraph naming the
connective tissue across all briefs. This is what stops the campaign from
looking like four different brands.

**Skill dependency:** Call `content-marketer` persona for the strategic
phrasing on the big idea + insight fields. Don't outsource the whole brief
to it, just borrow the elite-strategist voice for those two fields.

**Voice gate:** Yes (and `content-marketer`'s output must also pass the
Selr ban-list).

### Stage 4: 4-Week Launch Plan (`prompts/04-launch-plan.md`)

**Goal:** Single rollout calendar covering pre-launch (Week 0), launch
(Week 1), sustain (Week 2), optimise (Week 3). Owner column blank, the
user fills.

**Per-week table columns:** Day, Asset / Action, Channel, Owner, Status.

**Rules:**

- Each row is a single shippable thing. Not "do influencer outreach" ,
  instead "DM 12 nano-tier handles from segment 2 list".
- Prefer fewer, higher-impact rows over filler. A clean week beats a busy
  one.
- Reuse Stage 2 cross-segment leverage, call out which row is a re-cut of
  an earlier asset.
- For Selr workshop campaigns, the Week 1 launch row should anchor to the
  workshop date; Week 2 sustain feeds Skool conversion sequence.

**Footer (mandatory):** Kill criteria, 3 numeric thresholds at which the
campaign cuts or pivots. (e.g. "If CTR <0.6% on hero by Day 5 → swap
headline." or "If <30 workshop registrations by T-14 → kill paid and triple
organic frequency.")

**Voice gate:** Yes. Owner column stays blank to keep agency.

**Skill dependency:** If any row says "ship landing page", note to call
`copywriting` skill for that handoff. If any row says "ship ad set", note
`ad-creative`. These are handoff stubs, the launch plan doesn't generate
the assets, it sequences them.

### Stage 5: Social Posts (`prompts/05-social-posts.md`)

**Goal:** 5-8 posts per segment. Each post = caption + format + surface +
Higgsfield prompt (if visual) + why-this-works one-liner.

**Per-post fields:**

- Surface (Instagram Reels / IG carousel / TikTok / YouTube Short / X post /
  LinkedIn)
- Format (9:16 video / 4:5 carousel / 1:1 still / 15s vertical)
- Hook (first 1.5s of video, or first line of caption)
- Caption (voice-graded, Selr-banned phrases stripped)
- On-screen text bands (if video)
- Higgsfield prompt (paste-ready, using image or video skeleton)
- Why this works for this segment (one sentence)

**Distribution rules (per segment):**

- 60% concept-driven (insight from creative brief)
- 30% utility (how to use / what fits / where it goes)
- 10% brand POV
- At least one post per segment is a single-take, no-cut shot (gives
  Higgsfield image-to-video an anchor it can run on)
- At least one post per segment ends on a CTA the user can A/B test (the CTA
  is named, not generic, e.g. "Comment WORKSHOP for the city list" not
  "DM for info")

**Carousel handoff (critical):** For any post flagged as "IG carousel", DO
NOT render slides via Higgsfield for Selr-brand runs. The Higgsfield prompt
field for carousels says: "Carousel → carousel-generator (Remotion +
Fraunces hand-typeset). Higgsfield only supplies background imagery for
slide 4 or slide 7 if requested." Document the carousel-generator template
that fits (see `carousel-generator` skill's 15 templates).

**CTA wiring:** For any CTA that drops a community asset (Notion page, repo,
tool), pre-stage the GitHub → Notion → ManyChat pipeline via the
`community-drop` skill (which implements the canonical pattern documented
at `~/.claude/projects/-Users-luke/memory/community-publishing-pipeline.md`).
Note the keyword in the post so ManyChat can trigger.

**Summary footer (mandatory):**

- Asset count by format (video vs still vs carousel)
- Which posts re-cut which others (re-use map)
- The 3 hero posts to spend paid amplification on (and which paid platform
  fits each, Meta / TikTok / LinkedIn / YouTube)

**Skill dependencies:**

- `direct-response-copy` for DR-style hook lines
- `alex-hormozi-content-method` for volume structure + 3P opener
- `social-content` for per-platform format/timing guidance
- `ad-creative` for the 3 hero posts' paid headline variants
- `carousel-generator` for carousel handoffs (note the template choice)

**Voice gate:** Yes, every caption and every on-screen text band.

### Stage 6: Influencer Army (`prompts/06-influencer-army.md`)

**Goal:** Tiered influencer plan (macro / micro / nano), with the user
over-indexing on micro and nano (small-brand reality).

**Per-tier fields:**

- Definition for this campaign (follower band + posting cadence assumption)
- Why this tier (or why we're skipping it), 1-2 sentences
- Table: Handle, Platform, Niche fit (1-10), Why they fit, Content angle for
  THIS brand, Risk flags

**Table rules:**

- 6-10 handles per tier (fewer for macro if skipping)
- Niche fit ≥7 or don't list
- "Content angle" = the specific thing this creator should make, not "post a
  Reel". Example: "Behind-the-scenes 30s of the moment she opens her laptop
  and runs the GHL setup skill at 6am before her staff arrive, tumbler in
  frame for 8 of 30s."
- Risk flags = controversial past content, recent sponsor stack overlap,
  audience mismatch, anti-AI public stance

**Per-handle DM:** Use `templates/outreach-dm.md` as structural reference.
Do NOT copy-paste, every DM names something specific from that creator's
recent work. AU-adapted voice (no US influencer norms like "let's hop on a
call", no "let's chat synergy"). 5-beat shape (earned opener / why we fit /
concrete ask / what's in it for them / easy out). Max ~70 words.

**Per-handle brief (5-8 lines):**

- Concept
- Deliverables (quantity + format + posting window)
- Required brand cues (product visibility, hashtag, link sticker)
- Compensation framework (product-only / fee + product / fee + commission)
- Usage rights (what we can re-cut and run as paid)
- Approvals (what we'll review pre-post, or "post first, no approval" if it
  fits the creator)

**Footer (mandatory):** Kill list, 2-4 handles you considered and
explicitly cut, with one-line reason each. Stops the user from going back to
those handles and wasting outreach cycles.

**Handoffs (post-stage, automated):**

1. **Write to GHL**, Call `ghl-crm` to create each listed influencer handle
   as a contact in the workshop city's tag, with the tier as a sub-tag (e.g.
   `influencer-micro-melbourne-2026-06`). Custom field `content_angle` =
   the brief. Custom field `dm_status` = "drafted".
2. **Write to Notion**, Call `Notion:create-page` to create a campaign
   page under the user's "Influencer Campaigns" parent, with one toggle
   block per handle containing the DM + brief + content angle.
3. **Surface to user**, Show the user the GHL contact list URL + the Notion
   page URL. They send the DMs from there (no auto-send from this skill).

**Voice gate:** Yes, DMs and briefs both pass the Selr ban-list.

### Stage 7: Aggregated Higgsfield Prompts (`prompts/07-higgsfield-prompts.md`)

**Goal:** A single clean file containing every Higgsfield prompt from Stages
5 and 6, reformatted for paste-ready use in the Higgsfield UI.

**This is the demo paste target.** When the user is on camera running
through the Higgsfield UI, they paste from this file. Make it clean.

**File structure:**

```markdown
# Higgsfield Prompts: <Brand>, <YYYY-MM-DD>

Aggregated from Stages 5 (Social Posts) and 6 (Influencer Briefs).
Paste each block straight into the Higgsfield UI. The skill that emitted
this file: `higgsfield-cmo-agent` v1.0.0.

## Stage 5: Social Post Prompts

### Segment 1: Post 1, <Surface, Format>

[Full Higgsfield prompt, no surrounding commentary]

### Segment 1: Post 2, <Surface, Format>

[Full prompt]

...

## Stage 6: Influencer Reference Shots (optional)

### @handle (Tier: micro): Concept reference shot

[Full prompt]

...

## Notes

- Carousel posts: rendered via carousel-generator, not Higgsfield.
- Where a post is X/LinkedIn-text-only, no prompt is listed.
- Each prompt is voice-graded (Stage 5) and brief-aligned (Stage 3).
```

**Aggregation rules:**

- One prompt per code block.
- Code block fenced, no language tag.
- Header above each prompt names the segment + post + surface + format so the
  user can find which prompt is which on the fly.
- Skip carousel posts (they aren't Higgsfield-rendered).
- Skip text-only posts (X / LinkedIn text-only).

**No voice gate**, this is a mechanical reformat. The prompts inside have
already been voice-graded in Stages 5-6.

---

## Mid-Run Stage Jump (Resume Behaviour)

If the user says "skip to stage 5" or "jump to influencer army", do not
silently start. Check whether upstream stages have been written to the
output directory:

```bash
ls ~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/
```

If 00-04 are present, proceed. If any are missing, surface a one-line
warning ("Stages 1-3 not written, they're the source for Stage 5. Generate
those first?") and offer to run the missing stages.

If the user explicitly says "yes skip them, run 5 standalone", do it, but
emit weaker output and flag at the top of the file that upstream context is
synthesised on the fly, not anchored to the project's segments/briefs.

---

## Run Modes

### Full-Pipeline Mode (Default)

Run Stages 0 → 7 in sequence. Write each file, voice-gate as it goes. At the
end, surface to the user:

- The output directory path
- Stage 7's file path (the paste target)
- The GHL contact tag (Stage 6 handoff)
- The Notion page URL (Stage 6 handoff)
- A one-liner per stage of what got produced

Typical wall time: 15-25 minutes for a 4-segment campaign with 6 posts per
segment and 8 influencers per tier across 2 tiers.

### Single-Stage Mode

User says "just run stage 5 for the campaign in
~/board/_active/cmo-agent-selr-ai-2026-05-24/". Re-read 00-04 from disk,
run Stage 5, voice-gate, save. Do not touch other stages.

### Brief-Only Mode (Stage 0 in isolation)

User says "build me a brief for [brand]", run Stage 0 only, save
00-brief.md, stop. Useful when the user wants to refine the brief manually
before running 1-7.

### Re-Voice Mode

User says "re-grade Stage 5 against the voice gate", re-read 05-social-posts.md,
pipe each caption + on-screen text through `content-engine` + `humanizer`
again, re-save. Useful after the Selr ban-list updates.

---

## Examples

### Example 1: Selr AI Workshop Launch (Default Run)

User: *"Build me a marketing campaign for the next Selr AI workshop in
Melbourne."*

Skill behaviour:

1. **Stage 0**, Auto-load Selr defaults from
   `selrai-business-model.md` + `brand-contact-urls.md`. Capture: offer =
   workshop, city = Melbourne, goal = registrations, date window = next
   Melbourne workshop date. Write `00-brief.md`.
2. **Stage 1**, 4 segments: AU SMB operators (REPEAT, workshop → Skool
   pipeline), Solo founders building AI agencies (AMPLIFIER, word-of-mouth
   in indie founder Slack/Discord communities), Mid-career operators
   repositioning into AI roles, Hospitality + trades operators (regional
   variant). Rejected: "AI-curious students" (no buying power),
   "Enterprise IT" (wrong fit for workshop format).
3. **Stage 2**, Channel plan: IG Reels + LinkedIn for SMB operators;
   YouTube long-form + IG Reels for solo founders; etc. Amplifier row for
   each = micro-influencer outreach + workshop attendee UGC.
4. **Stage 3**, 4 creative briefs, all anchored on the throughline "AU
   operators installing AI in their own businesses live in the room, not
   prompts on a slide deck".
5. **Stage 4**, 4-week plan ending on the Melbourne workshop date. Kill
   criteria: <30 paid registrations by T-14 → kill paid, triple organic
   frequency; <0.6% CTR on hero by Day 5 → swap headline; <40% workshop →
   Skool conversion → review the close, not the front-end.
6. **Stage 5**, 24 posts total (6 per segment), with paste-ready Higgsfield
   prompts for the video and still posts. Carousel posts hand off to
   `carousel-generator` with template choices noted.
7. **Stage 6**, 3 tiers: macro (skipped, too expensive for the test
   campaign), micro (8 handles across AU founder / SMB ops / trades
   creators), nano (10 handles in the Melbourne local creator pool).
   DMs drafted, briefs ready. Handles written to GHL + Notion page created.
8. **Stage 7**, Aggregated file with ~18 paste-ready Higgsfield prompts
   (24 posts minus carousels and text-only). User pastes into Higgsfield
   UI on camera.

Output dir: `~/board/_active/cmo-agent-selr-ai-2026-05-24/`

### Example 2: Generic Brand (Insulated Cup Stub)

User: *"Use the cmo-agent skill on the insulated cup brand stub and produce
the full campaign."*

Skill behaviour:

1. **Stage 0**, Run intake interview, but since the user said "use the
   stub", load `examples/selr-ai-workshop-brand-stub.md` instead. Wait,
   that's Selr-specific. Tell the user: "The Selr stub is for Selr brand.
   For a generic insulated cup demo, want me to use Hewitt's original cup
   stub at /tmp/hewitt-higgsfield-skills/skills/cmo-agent/examples/insulated-cup-brand-stub.md?"
2. If yes, proceed with that stub (US English, generic brand, no Selr ban
   list, but still no em dashes and still humaniser pass).

### Example 3: Stage Jump

User: *"Jump to stage 6 for the cmo-agent-selr-ai-2026-05-24 campaign and
update the micro tier with these 3 new handles."*

Skill behaviour:

1. Re-read 00-05 from disk.
2. Re-run Stage 6 with the new handles added.
3. Voice-gate, save, re-run handoffs (GHL + Notion update, not duplicate).
4. Note in the file what changed vs the previous run.

---

## Failure Modes

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| Stage 1 outputs 3 generic personas | Brief too thin, Stage 0 didn't capture enough detail | Re-run Stage 0, push for specifics on JTBD + buying trigger |
| Stage 2 channel plan suggests 4 primary channels per segment | LLM ignored the max-2 constraint | Re-run Stage 2 with explicit "MAX 2 PRIMARY" header in the prompt |
| Stage 3 throughline doesn't connect | Briefs are 4 different brands | Identify the shared customer truth across segments, rewrite throughline |
| Stage 4 kill criteria are squishy | "If engagement is low", not numeric | Force numeric thresholds (CTR %, registrations N, conversion %) |
| Stage 5 posts feel agency-generic | Voice gate didn't fire | Re-run Stage 5 explicitly through `content-engine` + `humanizer` |
| Stage 5 has 24 carousels and 0 videos | LLM picked the easy format | Re-run Stage 5 with format distribution constraint (≥40% video) |
| Stage 6 DMs sound templated | "Hi [name]" / "love your content" | Re-write each DM with a specific reference to a recent post from that creator |
| Stage 7 includes Stage 5 carousel posts | Aggregator didn't skip carousels | Re-run Stage 7 with explicit skip-rule on format = carousel |
| GHL write fails | `ghl-crm` skill not installed or auth expired | Surface to user, install via `ghl-mcp-setup` or refresh auth |
| Notion write fails | `Notion:create-page` skill not connected | Surface to user, install via Notion skill auth |
| Higgsfield MCP not connected when previews requested | `higgsfield-connector` not run | Surface to user, install via `higgsfield-connector` skill; campaign still saves prompt-only |

---

## What This Skill Will Never Do

- **Auto-send DMs.** It writes them to GHL + Notion for the user to send.
  Never sends them via any channel automatically. (Sister rule to the
  "verify URLs before blasting" + "show Luke before any blast" hard rule.)
- **Render Selr-brand carousels in Higgsfield.** Carousels are Remotion +
  Fraunces via `carousel-generator`. Higgsfield only supplies background
  imagery for slide 4 / slide 7.
- **Promise outcomes in copy.** No "you'll grow X%". No "guaranteed
  registrations". No "this campaign will close N deals". Process language
  only.
- **Use personal life material.** No "my family" / "my kids" / "my morning
  routine" in any caption, DM, brief, or strategy line. Hard firewall.
- **Add em dashes.** Replaced with commas, full stops, or rewritten clauses.
- **Promise refunds.** No money-back / 30-day refund / satisfaction
  guarantee. The conviction layer comes from price transparency + named
  mechanism + real testimonials, not refunds.
- **Promise drop-in chats.** No "come say hi at the workshop". No "swing
  past for a coffee". Every unpaid chat displaces a $1,500 scoping call.
- **Mint Higgsfield tool names.** Always ToolSearch for the current names
  before calling. Tool names drift between MCP releases.
- **Flip a repo public.** If Stage 5 references a community drop and the
  repo doesn't exist yet, it asks for explicit one-shot permission to
  create as private, then notes the public-promote step as a manual gate
  for the user.

---

## Style Constraints (Selr AI House Style)

When the brand is Selr AI (auto-loaded defaults), every output file follows:

1. **AU English**, colour, optimise, specialise, organisation, realised.
2. **No em dashes**, replaced with commas or full stops.
3. **Ban-list**, see Extended Ban-List above. Hard firewall on all 7
   categories.
4. **Voice**, confident, direct, no hype. Treats the customer as
   competent. Think operator talking to operator. No Instagram-fitness
   energy.
5. **Workshop framing**, "hands-on install" not "transformation". "Walk
   through together" not "you'll have a working system before you leave".
6. **Pricing transparency**, workshop $1,500 AUD shown upfront, never
   buried. Skool $499/mo USD with 3-month lock-in shown clearly.
7. **AU mobile / SMB-operator references**, Brisbane, Gold Coast,
   Melbourne, Sydney. AU dollars in copy. No US-centric examples ("CrossFit
   in Austin") unless the campaign specifically targets US.

For non-Selr brands, the skill respects whatever house style is captured in
the Stage 0 brief, but the no-em-dash rule applies universally (Luke runs
the skill).

---

## Routing Constraint (Avoid Overlap)

This skill must NOT poach triggers from:

- **`content-marketer`**, that's persona-only ("act as my CMO"). This
  skill is the orchestrated pipeline ("build me a campaign").
- **`marketing-agency`**, that's the top-level brain skill for marketing
  agency-style work. This skill is the Higgsfield-stack-specific orchestrator.
- **`higgsfield-marketing-studio`**, that's the one-prompt-to-campaign
  flow for a single asset bundle. This skill is the multi-channel,
  multi-segment, multi-week pipeline.
- **`higgsfield-content-factory`**, that's the 60-day carousel calendar.
  This skill emits posts inside a campaign, not a standalone carousel
  factory.
- **`ad-creative`**, that's bulk ad copy iteration. This skill calls into
  it for Stage 5's hero-3-paid posts but doesn't replace it.

When in doubt, route on these phrases:

- "build a campaign", "multi-channel campaign", "give me an influencer
  army", "describe the ideal customer + give me the plan" → this skill
- "act as my CMO and review X" → `content-marketer`
- "marketing agency-style work" → `marketing-agency`
- "one-prompt-to-campaign for [single asset bundle]" →
  `higgsfield-marketing-studio`
- "60-day carousel calendar" → `higgsfield-content-factory`
- "iterate ad headlines" → `ad-creative`

---

## File Layout (Skill Source)

```
higgsfield/skills/higgsfield-cmo-agent/
├── SKILL.md                              (this file)
├── prompts/
│   ├── 00-brief.md                       (intake OR Selr-default loader)
│   ├── 01-segments.md                    (3-5 segments + REPEAT/AMPLIFIER + rejected footer)
│   ├── 02-channel-plan.md                (per-segment table + cross-segment leverage)
│   ├── 03-creative-brief.md              (big idea, message hierarchy, visual direction, do/don't, throughline)
│   ├── 04-launch-plan.md                 (4-week rollout, owner column blank, kill criteria)
│   ├── 05-social-posts.md                (5-8 posts per segment, each w/ caption + Higgsfield prompt + why-it-works)
│   ├── 06-influencer-army.md             (tiered table + personalised DMs + per-handle briefs + kill list)
│   └── 07-higgsfield-prompts.md          (AGGREGATED, every prompt from Stages 5+6 in one paste-ready file)
├── templates/
│   ├── higgsfield-image-prompt.md        (refs shared Skeleton 1, brand-defaulted to Selr if applicable)
│   ├── higgsfield-video-prompt.md        (refs shared Skeleton 2)
│   ├── outreach-dm.md                    (5-beat shape, AU adapted)
│   └── segment-card.md                   (segment_name, size_guess, painpoints, flag, sample_messages)
└── examples/
    └── selr-ai-workshop-brand-stub.md    (demo seed for Selr AI workshop campaign)
```

---

## Demo Command

```text
Build me a complete multi-channel marketing campaign for the next Selr AI
workshop in Melbourne. Run all 8 stages including the influencer army and
the aggregated Higgsfield prompts file.
```

Expected: the skill auto-loads Selr defaults, runs Stages 0-7, writes 8
files to `~/board/_active/cmo-agent-selr-ai-<YYYY-MM-DD>/`, surfaces the
output dir + Stage 7 paste-target path + GHL contact tag + Notion page URL.

Or, for a generic demo:

```text
Use the cmo-agent skill on the insulated cup brand stub at
/tmp/hewitt-higgsfield-skills/skills/cmo-agent/examples/insulated-cup-brand-stub.md
and produce the full campaign including the influencer army.
```

---

## Higgsfield MCP Runtime Contract

The skill calls into the Higgsfield MCP via `ToolSearch` at run-time. Never
hardcode tool names, they drift between MCP releases.

### Runtime discovery

When the user requests live previews of a Stage 5 or Stage 6 prompt:

1. Call `ToolSearch` with query `higgsfield`.
2. Read the returned tool catalogue (typically includes a text-to-image
   tool, image-to-video tool, video-to-video tool, and an upload tool).
3. Match the prompt's asset type to the right tool:
   - 9:16 / 16:9 / 4:5 / 1:1 still → text-to-image tool
   - 5-8s video → text-to-video or image-to-video tool
   - Multi-chunk video → call the video tool once per chunk
4. If no matching tool exists in the catalogue, surface to user:
   "Higgsfield MCP tool for [asset type] not found in current catalogue ,
   save the prompt for paste-only and re-try after `higgsfield-connector`
   updates."

### Connection precondition

If `ToolSearch` for `higgsfield` returns zero results, the MCP isn't
installed or auth has expired. Surface:

```
Higgsfield MCP not connected. Campaign will save prompt-only (no live
previews). To enable previews, run the `higgsfield-connector` skill.
This campaign run is otherwise complete.
```

Then continue the run prompt-only, the campaign output is still complete
without live previews.

### Preview gating

Live previews are OPT-IN per run. Default behaviour is prompt-only (saves
credits, faster turnaround). User opts in by saying:

- "render previews for the hero 3"
- "preview Stage 5 Segment 1 prompts"
- "render every Stage 5 video prompt"

Do not auto-render. Higgsfield credits cost money, the skill respects the
user's budget.

### Element tag prerequisite

If any prompt uses an `@element` tag (`@product`, `@logo`, `@founder`),
the tag must be set up in the Higgsfield Elements panel BEFORE rendering.
See `../shared/element-tagging.md` for setup.

If a prompt references a tag and the tag isn't set up, surface:

```
Prompt for [post identifier] references @<tag> but the tag isn't set up in
Higgsfield Elements. Either set it up (see element-tagging.md) or remove
the tag reference and replace with literal description.
```

---

## Per-Offer Routing (Selr AI Variants)

Selr AI runs vary by which offer is the campaign anchor. Each offer has
distinct segment priorities, channel weighting, and copy emphasis.

### Workshop campaign (default: $1,500 AUD in-person, 12 seats)

- **Segments:** AU SMB operators (REPEAT), solo founders (AMPLIFIER),
  mid-career repositioners (NEITHER), hospitality/trades (REPEAT secondary).
- **Channel weighting:** IG @selr__ai + LinkedIn (Luke) heavy; X for
  founders; YouTube selective; email post-registration heavy.
- **Copy emphasis:** "in the room", "by 5pm", "12 operators, one install
  each", city-specific (Melbourne / Sydney / Gold Coast).
- **Anchor metric:** workshop registrations.
- **Kill criteria template:** if <30 paid regs by T-14 → kill paid + triple
  organic; if CTR <0.6% on hero by Day 5 → swap headline.
- **Sustain layer:** workshop → Skool conversion (target 40%) via the
  8-touchpoint workshop-to-Skool sequence.

### Skool Premium campaign ($499/mo USD, 3-month lock-in)

- **Segments:** Workshop alumni who haven't converted (REPEAT primary),
  Skool-curious founders who watch Luke's content (AMPLIFIER), trial-curious
  SMB ops (NEITHER).
- **Channel weighting:** Email (alumni list) heavy; IG @selr__ai for
  visibility; LinkedIn for thought-leadership; Skool community itself
  for in-feed retention.
- **Copy emphasis:** "what comes after the workshop", "the build calls
  with Harvey", "office hours with Luke", "the install drops every Mon
  Wed Fri".
- **NEVER bundle with workshop.** Skool is the ongoing layer; workshop
  close mentions it, doesn't include it.
- **Anchor metric:** Skool conversion % (from workshop attendees) AND
  Skool retention beyond month 3 (lock-in expires).
- **Kill criteria template:** if 30-day conversion <40% → review workshop
  close script; if month-3 retention <60% → audit Mon/Wed/Fri build drops.

### AI Systems Architecture (ASA) campaign (from $5K AUD, one-off install)

- **Segments:** AU mid-market companies 20-200 staff (REPEAT primary),
  workshop alumni who want the full install (AMPLIFIER), service
  businesses with manual back-office bottlenecks (REPEAT secondary).
- **Channel weighting:** LinkedIn (Mike + Luke) heavy for outbound; case
  study content on YouTube + LinkedIn; email to specific alumni segments.
- **Copy emphasis:** "one-off install", "no retainer", "your AI operating
  system, installed and handed over", "we leave, you own it".
- **Anchor metric:** ASA scoping calls booked → ASA proposals sent → ASA
  contracts signed.
- **Kill criteria template:** if <2 scoping calls booked per month → audit
  LinkedIn outbound cadence; if <50% scoping → proposal conversion → audit
  scoping script.
- **No public sales page.** ASA is sales-led; landing page is a referral
  surface only.

### High-end Consulting campaign (bespoke, sales-led, premium AU only)

- **Segments:** Named AU founder networks (Luke's warm relationships),
  ex-ASA clients with grown complexity, board referrals.
- **Channel weighting:** No paid. No public funnel. 100% relationship
  + referral.
- **Copy emphasis:** None public. Internal-only campaign tracking.
- **Anchor metric:** named conversations → scoped engagements.
- **Note:** This skill produces minimal output for High-end Consulting ,
  mostly internal opportunity-tracking notes. Surface to user that the
  channel plan stops at "warm relationship", not public campaign assets.

### Strategy Call campaign ($1,500 AUD, paid scoping conversation)

- **Segments:** SMB founders who don't fit workshop (wrong city, wrong
  date, wrong format), ASA-curious mid-market who need pre-engagement
  scoping, ad-hoc inbound.
- **Channel weighting:** LinkedIn (Luke) for visibility; ASA + workshop
  landing pages as routing surfaces.
- **Copy emphasis:** "paid scoping conversation", "we get to a recommendation",
  "applied as credit toward ASA if we proceed".
- **Anchor metric:** Strategy Call bookings.
- **Kill criteria template:** if <2 calls booked per month → audit
  routing CTAs on workshop + ASA pages.

---

## Cross-Skill Data-Passing Contracts

Stages 1-7 pass data to downstream skills through these explicit contracts.

### To `content-engine` (mandatory voice gate)

```yaml
input:
  text: "<stage output text>"
  brand: "selr-ai"   # or other brand slug
  language: "AU"     # or "US"
  ban_list_pack: "selr"   # loads Selr-specific banned phrases on top of universal
expected_output:
  graded_text: "<rewritten text if any axis failed>"
  axes_failed: ["slop", "support_promise", "outcome_guarantee", "drop_in", "personal_life", "em_dash", "english_mismatch"]
  passes: true | false
```

If `passes: false`, re-run stage with the failure axes named in the
re-prompt. Do not save a failing draft.

### To `humanizer` (mandatory slop gate)

```yaml
input:
  text: "<stage output text, already content-engine-graded>"
expected_output:
  rewritten: "<text with signs-of-AI-writing patterns stripped>"
  patterns_detected: ["inflated_symbolism", "promotional_adjective", "vague_attribution", "rule_of_three", "ai_vocabulary", "negative_parallelism"]
```

Always pipe content-engine output through humanizer (in that order).
Content-engine handles brand voice; humanizer handles generic AI patterns.

### To `carousel-generator` (Stage 5 carousel handoff)

```yaml
input:
  template: "5-tips" | "case-study" | "myth-bust" | "stack-reveal" | etc.
  slides:
    - slide_number: 1
      type: "hook"
      headline: "<voice-graded>"
      subhead: "<voice-graded>"
      body: "<voice-graded>"
    - slide_number: 2
      ...
  brand_palette: "selr-purple-accent"
  output_path: "~/board/_active/cmo-agent-<slug>-<date>/carousels/<post-id>/"
expected_output:
  pngs: ["slide_1.png", "slide_2.png", ...]
  caption_file: "caption.md"
```

Stage 5's post spec writes the slide structure inline; carousel-generator
renders the PNGs in the output dir alongside the campaign.

### To `ghl-crm` (Stage 6 contact write)

```yaml
input:
  contacts:
    - name: "<display_name or @handle>"
      source: "influencer-outreach"
      tags:
        - "influencer"
        - "tier-<macro|micro|nano>"
        - "campaign-<brand-slug>-<date>"
        - "city-<city if applicable>"
      custom_fields:
        content_angle: "<from brief>"
        dm_status: "drafted"
        platform: "<IG|X|YT|TikTok|LinkedIn>"
        handle_url: "<full URL>"
        tier: "<macro|micro|nano>"
expected_output:
  contacts_created: N
  contacts_updated: N (if some already existed)
  ghl_tag_url: "<URL to filter GHL by this campaign tag>"
```

If any contact write fails, log the failure but continue with the others.
At the end, surface the count of successes vs failures to the user.

### To `Notion:create-page` (Stage 6 campaign page)

```yaml
input:
  parent: "Influencer Campaigns"   # or fallback to ~/Vault/Projects if Notion absent
  title: "Influencer Campaign, <Brand>, <YYYY-MM-DD>"
  body_blocks:
    - heading_1: "Brief"
    - link: "<00-brief.md path>"
    - heading_1: "Tiers"
    - toggle:
        title: "Macro"
        body_blocks: [...]   # one sub-toggle per handle
    - toggle:
        title: "Micro"
        body_blocks: [...]
    - toggle:
        title: "Nano"
        body_blocks: [...]
    - heading_1: "Kill List"
    - bulleted_list: [...]
    - heading_1: "Status Tracker"
    - to_do_list:
        - "DMs sent: 0 / N"
        - "Replies: 0 / N"
        - "Confirmed yeses: 0 / N"
        - "Content posted: 0 / N"
expected_output:
  notion_page_url: "<URL>"
  page_id: "<Notion page ID>"
```

### To `community-drop` (Stage 5 + 7 CTA wiring)

```yaml
input:
  drop_name: "<descriptor>"
  keyword: "<ManyChat trigger keyword>"
  asset_repo: "<GitHub repo slug under lukeselr>"
  notion_page: "<existing or to-be-created>"
  manychat_flow: "<flow name to wire trigger into>"
expected_output:
  repo_url: "<GitHub URL>"
  notion_url: "<Notion URL>"
  manychat_flow_url: "<ManyChat URL>"
  trigger_keyword_active: true
```

Only called when Stage 5 posts include a community-drop CTA. Skip
otherwise.

---

## Selr Ban-List Audit Table (Per-Stage Validator)

Every stage's voice gate runs this audit table. If ANY row fails, the
stage doesn't save until rewritten.

| Pattern | Where it appears | Auto-fix |
|---------|-------------------|----------|
| Em dash (,) | Anywhere | Replace with comma + space, or full stop |
| "transform your business" | Captions, briefs, headlines | Rewrite: "install one workflow that removes the bottleneck" |
| "10x" | Anywhere | Rewrite with specific multiplier or remove |
| "game-changer" | Anywhere | Remove. Replace with specific named change |
| "next-level" | Anywhere | Remove. Replace with specific named outcome |
| "scale to N figures" | Captions, briefs | Remove. Replace with the specific operational change |
| "guaranteed" | Anywhere | Hard-fail. Outcome guarantees banned |
| "money-back" | Anywhere | Hard-fail. Refund language banned |
| "30-day refund" | Anywhere | Hard-fail. Refund language banned |
| "come say hi" | CTAs | Hard-fail. Drop-in invites banned |
| "swing past" | CTAs | Hard-fail. Drop-in invites banned |
| "we'll always be here" | Captions, emails | Hard-fail. Support promise banned |
| "weekly Q&A" | Captions, emails | Hard-fail (workshop), allowed (Skool) |
| "ongoing support" | Captions, emails | Hard-fail (workshop), allowed (Skool with caveat) |
| "my family" / "my kids" / "my wife" | Anywhere | Hard-fail. Personal life off-limits |
| "my morning routine" | Anywhere | Hard-fail. Personal life off-limits |
| US English in Selr run | Anywhere | Replace: color → colour, optimize → optimise, organization → organisation, realize → realise |
| "secret sauce" | Anywhere | Remove. Replace with the named mechanism |
| "elevate" | Anywhere | Remove. Replace with specific verb |
| "supercharge" | Anywhere | Remove. Replace with specific verb |
| "unlock" | Anywhere | Remove. Replace with specific verb |
| "AI-powered" | Anywhere | Remove. State which AI is doing what |
| "transform" (as verb) | Anywhere | Replace with the specific change |
| "hop on a quick call" | DMs | Remove. They haven't said yes yet |
| "love your content" | DMs | Hard-fail. Specific recent-work reference required |
| "Hi [name]!" | DMs | Hard-fail. Personalised opener required |
| "amazing" / "incredible" | Anywhere | Remove. AU-direct voice |
| "let's go!" | Anywhere | Remove. US influencer-coach voice |

For non-Selr runs, only the universal rows apply (em dash, refund,
guarantee, US-vs-AU-mismatch-if-AU-was-specified).

---

## See Also

- `../shared/higgsfield-prompt-skeletons.md`, canonical Skeletons 1-5
- `../shared/element-tagging.md`, `@product` consistency primitive
- `../shared/hook-bank-100.md`, 100 hooks across 10 archetypes for Stage 5
- `~/.claude/projects/-Users-luke/memory/selrai-business-model.md`, V4.1.2
  brand defaults
- `~/.claude/projects/-Users-luke/memory/brand-contact-urls.md`, Selr URL
  registry
- `content-engine`, voice ship-gate
- `humanizer`, slop ship-gate
- `ghl-crm`, influencer handle write-back
- `community-drop`, CTA wiring skill (GitHub → Notion → ManyChat). Canonical
  pattern documented at `~/.claude/projects/-Users-luke/memory/community-publishing-pipeline.md`
- `Notion:create-page`, campaign page creation
- `carousel-generator`, Selr-brand carousel rendering (Remotion + Fraunces)
- `direct-response-copy`, DR-style hook copy for Stage 5
- `ad-creative`, paid headline variants for the hero 3 in Stage 5
- `email-content-engine`, email channel handoff for Stages 2 + 4
- `content-marketer`, elite strategist persona for Stage 3 big idea +
  insight fields
- `alex-hormozi-content-method`, volume + structure for Stage 5
- `social-content`, per-platform organic routing for Stage 5
