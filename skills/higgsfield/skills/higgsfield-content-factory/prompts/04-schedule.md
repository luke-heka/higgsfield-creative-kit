# Stage 4: Schedule (Optional)

Hand off completed carousels to a scheduling tool. Only invoked if the
user explicitly asks to schedule. Default behaviour: write paste-ready
captions + slide paths the user manually schedules.

## When to invoke

ONLY when the user says one of:

- "schedule the carousels"
- "push them to Meta MCP"
- "queue them up in [tool]"
- "wire up the ManyChat trigger" (specific to slide-7 CTA carousels)

NEVER auto-invoke after Stage 3. Stage 3 ends with rendered slides on
disk. The user owns the publishing decision.

## Inputs

- Path to a completed batch folder
  (`~/board/_active/content-factory-<DATE>/03-generate/batch-<N>/`)
- `scheduler` (required), one of:
  - `meta-mcp`, Meta Ads MCP for IG/FB
  - `omnisocials`, cross-platform scheduler
  - `manual`, write paste-ready files, no MCP call
- `manychat_handoff` (optional, default false), if any carousel has
  "Comment WORD" CTA on slide 7, wire ManyChat trigger

## Pre-flight confirmation

```
About to schedule batch <N> (5 carousels) via <scheduler>.
- Carousels: <list of slugs>
- Target dates: <from Stage 2 calendar>
- ManyChat handoff: <yes / no>

Proceed? (yes / adjust / cancel)
```

## Field-by-field actions

### 4.1: Route by scheduler

**If `scheduler: manual`:**

Write `04-schedule.md` with for each carousel:

```markdown
## <slug>: schedule for <date> @ <time> AEST

**Slide PNGs:** ~/board/_active/.../batch-<N>/<slug>/rendered-slides/
**Caption:**

<paste-ready caption from caption.md>

**ManyChat trigger (if applicable):** Comment "<WORD>" → DM <ASSET>
```

Done. User manually schedules.

**If `scheduler: meta-mcp`:**

1. `ToolSearch` query `meta-ads`, find the IG scheduling tool.
2. For each carousel:
   - Call `mcp__meta-ads__create_ad_creative` or the platform's
     scheduled-post tool with the slide PNGs + caption.
   - Set scheduled_publish_time to the Stage 2 calendar date.
3. Save the returned post IDs to `04-schedule.md` for audit.

**If `scheduler: omnisocials`:**

1. `ToolSearch` query `omnisocials`, find `create_post` or
   `create_and_publish_post`.
2. Per Stage 2 calendar:
   - Set workspace to the Selr AI workspace (487915_*) by default.
   - Add IG + FB channels.
   - Upload PNGs.
   - Set scheduled time.
3. Save returned post IDs.

### 4.2: ManyChat handoff (if any carousel has "Comment WORD" CTA)

For each carousel with a ManyChat CTA:

1. Read the CTA word from the caption (e.g. "Comment KIT to get the
   starter pack").
2. Confirm a ManyChat keyword trigger exists for that word. Run
   `mcp__manychat__growth_tool_list` or check `manychat-mcp-setup`.
3. If no trigger exists, run the `community-drop` skill (which wraps
   the community-publishing-pipeline workflow) to set one up. Defaults:
   - GitHub repo: matching kit/asset repo under `lukeselr`
   - Notion DM payload page: created per Notion notion-manychat-asset
     skill
4. Record the trigger word + asset URL in `04-schedule.md`.

### 4.3: Write `04-schedule.md`

```markdown
# Stage 4: Schedule

**Date:** <YYYY-MM-DD>
**Scheduler:** <meta-mcp | omnisocials | manual>
**Batch:** <N>
**Carousels scheduled:** <count>

## Schedule

| slug | scheduled date | time AEST | scheduler post ID | ManyChat trigger |
|---|---|---|---|---|
| ... |

## ManyChat handoff

- <trigger word> → <asset URL>
- ...

## Notes

- <Anything user should know, e.g. "IG post #3 paused at draft because
  caption length 2,210 chars (>2,200 limit). Trim 10 chars and re-run">
```

## Kill criteria

- Scheduler MCP returns auth error → STOP, route user to relevant
  `*-mcp-setup` skill.
- Caption exceeds platform limit (IG 2,200 chars; Threads 500) → STOP
  per carousel, ask user to trim.
- ManyChat trigger word collision (same word already assigned to a
  different asset) → STOP, ask user to pick a different word.
- More than one carousel in a batch is scheduled for the same minute →
  re-distribute. IG penalises burst posting.

## Rejected (do not do)

- ❌ Don't auto-publish (set scheduled_publish_time, don't call publish
  directly).
- ❌ Don't bypass the user approval gate. Even after Stage 3 "done",
  Stage 4 needs its own "yes proceed".
- ❌ Don't push to public IG without showing the user the final caption
  + slide previews once more. Per the "show before any blast" rule.
- ❌ Don't push to the user's personal IG handle, they post there
  manually. Default workspace = the business brand account.

## MCP / dependency calls

- `meta-ads` MCP (if scheduler = meta-mcp)
- `omnisocials` MCP (if scheduler = omnisocials)
- `manychat` MCP (if manychat_handoff = true)
- `community-drop` skill (if a new ManyChat trigger needs setting up;
  wraps the community-publishing-pipeline workflow)
