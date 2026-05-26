# Stage 2: Plan

Turn the 20 research candidates into a 60-day production calendar with
per-carousel idea cards. No Higgsfield credits are spent at this stage.

## Inputs

- `01-research.md` from Stage 1 (mandatory)
- `cadence_per_week` (optional), defaults to 5 carousels / week
- `total_days` (optional), defaults to 60
- `posting_days` (optional), defaults to Mon-Fri
- `posting_time` (optional), defaults to 06:00 AEST

## Pre-flight confirmation

Before running, restate to the user:

```
About to plan a <total_days>-day carousel calendar.
- Niche: <niche from Stage 1>
- Cadence: <cadence_per_week> carousels / week (~<total>/<total_days> days)
- Templates: will pick from the 15 available per idea
- Output: ~/board/_active/content-factory-<TODAY>/02-plan.md
- No Higgsfield credit spend at this stage (planning only).

Proceed? (yes / adjust / cancel)
```

If "adjust", change cadence/days/time and re-confirm. Do not proceed
silently.

## Field-by-field actions

1. **Calculate slot count.** `total_slots = (total_days / 7) *
   cadence_per_week`, rounded down. Default = 60/7 * 5 ≈ 42 slots.

2. **Expand 20 candidates → N idea cards.** Some candidates fork into 2-3
   angle variants (e.g. "5 mistakes" + "5 fixes" + "5 myth-busts of the
   same topic"). Add forks until count ≥ slot count. Cap fork count at 3
   per source idea, avoid topic fatigue.

3. **Assign template per idea card.** Use this routing table (also in
   SKILL.md):

   | post-type / intent | template |
   |---|---|
   | N tips | carousel-tips |
   | Cheat sheet | carousel-cheat-sheet |
   | Stack reveal | carousel-stack-reveal |
   | Case study with numbers | carousel-case-study |
   | Myth busting | carousel-myth-bust |
   | Common mistakes | carousel-mistakes |
   | Feature launch | carousel-feature-update |
   | Feature deep-dive | carousel-feature-spotlight |
   | Skill announce | carousel-skill-announce |
   | Skill card | carousel-skill-card |
   | Metaphor explainer | carousel-metaphor-explainer |
   | Prompt anatomy | carousel-prompt-anatomy |
   | Before/after | carousel-replace-this |
   | Reel cover | carousel-reel-cover |

   If none fits, default to `carousel-tips`.

4. **Sequence the calendar.** Rules:

   - Don't run the same template back-to-back. Stagger so format variety
     stays high (audience boredom is the #1 carousel killer).
   - Pace heavy-to-write templates (case-study, prompt-anatomy) once /
     week max, they take longer.
   - Front-load high-hook-score archetypes in week 1 (re-attract attention
     after any posting gap).
   - Save 1 slot / week for a reactive post the user can fill last-minute.

5. **Build full idea card per slot.** Use the `templates/idea-card.md`
   schema. Voice-grade every text field through content-engine +
   humanizer before saving.

6. **Group into Stage 3 batches.** Batch size = 5 carousels (one week's
   worth). Number batches sequentially (batch-01, batch-02, ...). The
   Stage 3 human gate runs per batch.

7. **Assign which carousels need Higgsfield supporting imagery.** Default:
   no Higgsfield image needed. Add Higgsfield only when the idea card
   slide 4 or slide 7 calls for a single supporting photo (e.g. a tool
   screenshot, a product hero shot, a setting backdrop). Mark with
   `higgsfield_image: true/false` on the card.

8. **Estimate credit budget.** For each card with `higgsfield_image:
   true`, budget ~50 credits per image (Nano Banana 2K or GPT Image 2.0).
   Sum total = `n_higgsfield_images * 50`. Convert to USD at Higgsfield's
   current rate (~$0.06/credit). Flag in 02-plan.md header.

## Output shape

Write to `~/board/_active/content-factory-<TODAY>/02-plan.md`:

```markdown
# Stage 2: 60-Day Carousel Calendar

**Date:** <YYYY-MM-DD>
**Niche:** <niche>
**Brand handle:** <handle>
**Cadence:** <cadence> carousels / week
**Total slots:** <N> across <total_days> days
**Posting times:** <days> @ <time> AEST

## Credit budget estimate

- Higgsfield images needed: <N>
- Estimated credits: <N * 50>
- Estimated USD spend: $<N * 50 * 0.06> across all batches

## Calendar

| date | day | batch | template | hook (one line) | higgsfield image? |
|---|---|---|---|---|---|
| 2026-05-26 | Mon | batch-01 | carousel-tips | "5 tools you can ditch when..." | no |
| ... |

## Idea cards (full)

### Slot 01: 2026-05-26, batch-01

[Full idea card per `templates/idea-card.md` schema]

### Slot 02: 2026-05-27, batch-01

[Full idea card]

...

## Reactive slot pool

One slot per week left empty for reactive content. User fills last-minute.

| week | reactive slot date | slot # |
|---|---|---|
| ... |

## Notes for Stage 3

- <Anything Stage 3 should know, e.g. "carousels marked higgsfield_image
  use the standard product hero shot, re-use the same Higgsfield image
  across batch-03, -04, -05 if visual is identical">
```

## Kill criteria

- <20 distinct ideas after fork expansion → STOP, ask user to extend
  research or accept shorter calendar.
- Same template repeats 3+ times in a row in the sequenced calendar →
  re-sequence.
- Estimated credit spend >$100 USD → flag and confirm with user before
  Stage 3.
- If you find yourself writing the same hook angle in 3 different cards,
  STOP. Drop one and add a new angle from the research output.

## Rejected (do not do)

- ❌ Don't auto-advance to Stage 3 without explicit "yes proceed".
- ❌ Don't skip voice-grading idea card hooks. The hook is 80% of the
  post's destiny.
- ❌ Don't bunch same-template days together. Variety beats efficiency.
- ❌ Don't budget Higgsfield images for every card. Most carousels need
  zero supporting imagery, only flag when the idea genuinely needs it.
- ❌ Don't put outcome guarantees in any card body ("you will get X
  results"). Process language only.

## MCP / dependency calls

- `alex-hormozi-content-method` (structure spine, load idea cards into
  hook + 5 tips + CTA scaffold)
- `content-engine` (mandatory ship-gate per text field)
- `humanizer` (mandatory ship-gate)
- `../../shared/hook-bank-100.md` (read-only, for archetype reference)
- `templates/idea-card.md` (schema reference for each card)
