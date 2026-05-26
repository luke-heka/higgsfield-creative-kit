# Stage 5: Cost Report

Pull Higgsfield credit spend across the run and compare against typical
agency and freelancer cost for the same volume. Output a readable receipt
the user can use for client sell or internal ROI documentation.

## Inputs

- Path to the run folder (`~/board/_active/content-factory-<DATE>/`)
- All `_summary.md` files from Stage 3 batches
- `currency` (optional), defaults to USD; convert to AUD on request

## Pre-flight confirmation

```
About to write the cost report for run <DATE>.
- Batches completed: <N>
- Carousels produced: <total>
- Higgsfield credits used: <total>
- Comparing against: agency cost, freelancer cost, in-house operator cost

Proceed? (yes / cancel)
```

## Field-by-field actions

### 5.1: Aggregate credit spend

Read every batch `_summary.md`. Sum:

- Total Higgsfield credits used
- Total carousels produced
- Total supporting images rendered
- Total slides rendered (carousel-generator output count, local
  rendering, $0 cost)

### 5.2: Compute Higgsfield USD cost

`higgsfield_usd = total_credits * 0.06` (Higgsfield rate ~$0.06/credit).

Cross-check against Higgsfield account billing if MCP allows
(`mcp__higgsfield__*`). If not, use the in-skill rate.

### 5.3: Compute comparison baselines

For the same volume of carousels:

**Agency cost**, typical creative agency rate:
- Carousel design: $200-$500 per carousel
- Caption writing: $50-$150 per caption
- Stock / custom imagery: $50-$200 per supporting image
- Total per carousel: ~$300-$850
- Estimate range: `total_carousels * [300, 850]`

**Freelancer cost**, typical Upwork/Fiverr senior rate:
- Carousel design + caption + image: $80-$200 per carousel
- Total range: `total_carousels * [80, 200]`

**In-house operator cost**, Selr AI internal rate:
- 1 hour per carousel at $50-$100/hr internal cost
- Total range: `total_carousels * [50, 100]`

### 5.4: Compute time saved

- Manual carousel (concept → design → caption → render): ~2 hours
- Factory carousel (user-time only, factory does the rest): ~10 min
- Time saved per carousel: ~1h 50min
- Total time saved: `total_carousels * 1.83 hours`

### 5.5: Voice-grade the executive summary

The opening 3-sentence summary at the top of the report is the highest
leverage text. Voice-grade through content-engine + humanizer.

NO hype phrases (banned vocab list in SKILL.md). Just numbers.

### 5.6: Write `05-cost-report.md`

```markdown
# Stage 5: Cost Report

**Run date:** <YYYY-MM-DD>
**Niche:** <niche>
**Carousels produced:** <total>
**Batches:** <N>

## Executive summary

This run produced <N> Instagram carousels at a Higgsfield credit cost of
$<higgsfield_usd>. Equivalent agency production would cost <$X to $Y>.
Equivalent freelancer production would cost <$X to $Y>. The factory ran
in <total_hours> hours of operator time vs <equivalent_manual_hours> for
the same manual output.

## Higgsfield spend

| line item | count | unit cost | total |
|---|---|---|---|
| supporting images (Nano Banana / GPT Image 2.0) | <N> | ~50 credits ($3 USD) | $<X> |
| credits used (raw) | <total> | $0.06 / credit | $<higgsfield_usd> |

**Total Higgsfield spend: $<higgsfield_usd>**

## Carousel-generator render

| line item | count | unit cost | total |
|---|---|---|---|
| slides rendered (Puppeteer, local) | <total> | $0 | $0 |

**Total render spend: $0**

## Comparison baselines

| production path | total cost range | per-carousel cost |
|---|---|---|
| **This factory (Higgsfield + carousel-generator)** | $<higgsfield_usd> | $<per_carousel> |
| Creative agency (full service) | $<low>–$<high> | $300–$850 |
| Senior freelancer | $<low>–$<high> | $80–$200 |
| In-house operator (Selr internal cost) | $<low>–$<high> | $50–$100 |

## Time saved

| metric | manual | factory | delta |
|---|---|---|---|
| operator time per carousel | ~2 h | ~10 min | 1h 50min saved |
| total operator time across run | <X h> | <Y h> | <X-Y> h saved |

## Notes

- Higgsfield credit cost assumes $0.06/credit at current Higgsfield rate.
  Cross-check against billing for invoice accuracy.
- Agency / freelancer ranges from 2025 market data (Australian + US).
- carousel-generator render cost is $0 because rendering runs locally on
  Puppeteer. No cloud render fees.
- Operator time excludes user time spent on Stage 2 idea-card review and
  Stage 3 batch approvals (~5 min per batch).

## Suggested next moves

- <If under-budget: "Run another batch, you have $X of headroom on the
  budget set in Stage 2.">
- <If over-budget: "Trim Higgsfield image use, only 2 of 8 batches
  needed supporting images. Consider zero-image carousels for next run.">
- <If schedule lag: "Auto-schedule via Stage 4 to recover the time
  saving.">
```

## Kill criteria

- Total Higgsfield spend exceeds Stage 2 estimate by >2x → flag at the
  TOP of the report in red, propose root cause.
- Credit-cost API unreachable AND in-skill rate stale → flag rate as
  "estimated, verify against billing".
- If any agency / freelancer comparison number looks made-up (e.g.
  "$10,000 saved" with no math) STOP and re-derive. The report's
  credibility depends on the math being right.

## Rejected (do not do)

- ❌ Don't inflate agency cost to make the saving look bigger. Use
  conservative real-market ranges.
- ❌ Don't include "Selr AI" pitch language in the report, this is a
  technical receipt, not a sales asset.
- ❌ Don't include phrases like "10x ROI" or "game-changing savings" ,
  banned vocab.
- ❌ Don't quote in AUD unless the user asked. Default = USD (matches
  Higgsfield billing).

## MCP / dependency calls

- `higgsfield` MCP (optional, billing cross-check)
- `content-engine` (mandatory ship-gate for executive summary)
- `humanizer` (mandatory ship-gate)
