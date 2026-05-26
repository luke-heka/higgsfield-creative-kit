# Stage 3: Generate (Batched + Human-Gated)

Produce carousels one batch at a time. Each batch = 5 carousels (one
week's worth). Per-batch human gate is non-negotiable, no batch starts
without explicit "yes proceed" from the user.

## Inputs

- `02-plan.md` from Stage 2 (mandatory)
- `batch_number` (required per invocation), which batch to generate now
- `dry_run` (optional, default false), if true, skip MCP calls, only
  build the artefacts to disk

## Pre-flight per-batch confirmation

Before each batch, restate:

```
About to generate batch <N> of <TOTAL_BATCHES> (5 carousels).
- Templates: <list per Stage 2 calendar>
- Higgsfield supporting images: <count of cards with higgsfield_image:true>
- Expected credit spend: ~<N images * 50> credits (~$<N*50*0.06> USD)
- Running total after this batch: $<cumulative> vs estimated total $<total>

Proceed? (yes / skip this batch / pause)
```

If the user says "pause", save state and exit cleanly. If "skip", advance
batch counter without generating. If "yes", proceed.

## Field-by-field actions per carousel within the batch

For each of the 5 carousels in the batch:

### 3.1: Load the idea card

Read the idea card from `02-plan.md`. Confirm:

- Template assignment exists and matches one of the 15 valid templates.
- Hook + body + CTA are present and voice-graded.
- `higgsfield_image: true/false` flag is set.

If anything missing, STOP and ask the user to update the card.

### 3.2: Build `carousel-template.json`

Look up the chosen template's schema. Each template has its own SKILL.md
at `~/.claude/skills/<template-name>/` that documents its config shape.

Populate the JSON slide-by-slide:

- Slide 1: hook (from idea card)
- Slides 2-6: body tips/cards (from idea card body section)
- Slide 7: CTA (from idea card CTA section)

Every text field MUST be voice-graded through content-engine + humanizer
before writing to JSON. Loop until pass.

### 3.3: Build supporting Higgsfield image (slide 4 or slide 7 only)

Only if `higgsfield_image: true` on the card.

Use **Skeleton 3** from `../../shared/higgsfield-prompt-skeletons.md`
(carousel slide image prompt, mobile-legible). NEVER use Higgsfield to
render the whole slide, only the background photographic element that
slots into the template's image field.

Image prompt structure:

```
4:5 VERTICAL INSTAGRAM CAROUSEL SLIDE, [SLIDE PURPOSE], visual concept: [...],
typography: none, image only (carousel-generator types the slide),
layout: [...], color palette: [3 anchors matching template's palette],
texture: [...], imagery: [...], mood: [2 adjectives],
brand cues: Selr AI purple accent subtle no logo,
EXCLUDE: stock photo people, gradient background, emoji, drop shadows,
hashtag overlays, watermark, typography (handled by carousel-generator),
AI-glossy skin, plastic shine, hyper-saturated colors
```

Then:

1. Call Higgsfield image MCP, `ToolSearch` query `higgsfield`, pick the
   image tool (Nano Banana / GPT Image 2.0 / Soul depending on subject).
2. If MCP call succeeds, save the returned image to
   `03-generate/batch-<N>/<carousel-slug>/supporting-image.png`.
3. Reference the image path in the carousel-template.json under the
   correct slide's image field.

If MCP is missing or call fails:

- Write the full image prompt to
  `03-generate/batch-<N>/<carousel-slug>/higgsfield-prompts.md`
  (paste-ready).
- Skip the image field in carousel-template.json (or use a transparent
  placeholder if the template requires one).
- Flag in the batch summary that manual rendering is required for this
  carousel.

### 3.4: Build the caption

Use `templates/caption-template.md` for shape. Inputs from idea card:

- Hook line (≤125 char, IG mobile cutoff)
- Body (3-5 lines of context, NO emojis unless idea card explicitly asks)
- CTA, single instruction, ideally "Comment WORD to get X" for ManyChat
  hand-off, or a soft "follow for more" if non-funnel
- Hashtags, 3-5 niche tags ONLY (not 8-15 generic, Selr AI house style)

Voice-grade the full caption through content-engine + humanizer. The
caption is the highest-leverage IG ranking signal, do not ship slop.

### 3.5: Render slides via carousel-generator

1. Confirm `carousel-generator` is installed, if not, STOP. Don't try to
   render slides any other way.
2. Pass the carousel-template.json to carousel-generator. Standard call:

   ```
   cd ~/.claude/skills/carousel-generator
   node render.js <path-to-template.json>
   ```

3. Output PNGs land in carousel-generator's output dir. Move them to
   `03-generate/batch-<N>/<carousel-slug>/rendered-slides/`.

### 3.6: Write the per-carousel folder

Final structure:

```
03-generate/batch-<N>/<carousel-slug>/
├── idea-card.md              (copy of the Stage 2 idea card)
├── carousel-template.json    (input for carousel-generator)
├── higgsfield-prompts.md     (if Higgsfield used or fallback fired)
├── supporting-image.png      (if Higgsfield rendered successfully)
├── caption.md                (paste-ready IG caption)
└── rendered-slides/          (PNG output from carousel-generator)
    ├── slide-01.png
    ├── slide-02.png
    └── ...
```

Slug = lowercase-hyphenated from the idea card's hook (first 5 words).

### 3.7: Update the batch ledger

Append to `03-generate/batch-<N>/_ledger.md`:

```markdown
- ✅ <slug>, template <template-name>, credits used <N>, voice-grade <pass>, render <ok>
```

## Post-batch summary

After all 5 carousels in the batch are done, write
`03-generate/batch-<N>/_summary.md`:

```markdown
# Batch <N> Summary

**Date:** <YYYY-MM-DD>
**Carousels produced:** 5
**Higgsfield credits used:** <N>
**USD cost (Higgsfield only):** $<X>
**Running total:** $<cumulative> / $<budget>

## Carousels in this batch

| slug | template | hook | higgsfield image | render status |
|---|---|---|---|---|
| ... |

## Issues / fallbacks

- <Anything that fell back to manual> 

## Next batch

Run Stage 3 again with `batch_number: <N+1>` after user approval.
```

Then ask the user: "Batch <N> done. Proceed to batch <N+1>? (yes / pause
/ stop)".

## Kill criteria

- carousel-generator missing → HARD STOP. Surface install instructions.
- Voice-grade fails 3 times on the same text field → STOP. Ask user to
  rewrite manually.
- Higgsfield credits used >2x batch estimate → STOP. Ask user before
  continuing.
- Any carousel-template.json fails to validate against the template's
  expected schema → STOP that carousel, write the issue to ledger, ask
  user.
- If you find yourself writing filler in any slide body, STOP. The
  template is wrong for this idea, go back to Stage 2.

## Rejected (do not do)

- ❌ Don't auto-advance to the next batch without user "yes proceed".
- ❌ Don't use Higgsfield to render a whole slide. Only supporting
  imagery for slide 4 / slide 7.
- ❌ Don't skip voice-grading any text field. Hook + caption are the two
  most important.
- ❌ Don't ship a carousel with unverified facts in the body. If a stat
  is unsourced, flag it and ask.
- ❌ Don't include "comment for support", "DM me for help", or "see you
  in DMs" CTAs, they trigger Selr AI's no-support-promise rule.
- ❌ Don't add emoji unless the idea card body explicitly asks. Default =
  no emoji.

## MCP / dependency calls

- `carousel-generator` (MANDATORY for slide rendering)
- One of 15 `carousel-*` templates per carousel
- `higgsfield` MCP (image generation, optional, fallback writes prompt)
- `content-engine` (mandatory ship-gate)
- `humanizer` (mandatory ship-gate)
- `../../shared/higgsfield-prompt-skeletons.md` (Skeleton 3 only)
- `../../shared/element-tagging.md` (if a recurring product appears
  across multiple carousels in the batch)
- `templates/caption-template.md` (caption shape)
