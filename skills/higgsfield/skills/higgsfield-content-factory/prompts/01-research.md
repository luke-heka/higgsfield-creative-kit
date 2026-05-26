# Stage 1: Research

Pull trending content in the user's niche. Output a single Markdown file
that Stage 2 (planning) can consume.

## Inputs

- `niche` (required), 1-2 sentence ICP, NOT a single word. Example:
  "AI for solo personal trainers in Australia who run their own gym".
- `brand_handle` (required), IG handle the carousels will publish under.
- `brand_voice_notes` (optional), defaults to Selr AI house voice.
- `time_window_days` (optional), defaults to 30.
- `n_competitors` (optional), defaults to 8.

## Field-by-field actions

1. **Restate niche and ask for narrowing if vague.** If `niche` is one
   word ("entrepreneurs", "marketers", "business owners"), STOP and ask
   the user for a 1-2 sentence ICP. Don't proceed with a vague brief.

2. **Identify 8 competitor / adjacent IG accounts.** List them as a
   Markdown table:

   ```
   | handle | one-line positioning | why relevant |
   ```

   If the user supplied competitors, use those. If not, ask them. Do NOT
   fabricate handles, flag any unverified ones with `(unverified)`.

3. **Pull trending posts via Apify.** Preferred call:

   ```
   ToolSearch query: apify
   Then: mcp__apify__apify--instagram-profile-scraper for each competitor handle
   resultsLimit: 20 per profile, last <time_window_days> days
   ```

   If Apify MCP is missing or returns nothing, fall back to
   `examples/sample-trending-fixture.json` and flag fixture mode at the
   top of the output file.

4. **Filter to carousels only.** Drop reels, single-image posts, stories.
   Only multi-slide static carousels, those are the format this factory
   produces.

5. **Rank top 20 by engagement.** Score = `(likes + 2*comments + 5*saves) /
   follower_count`. Save normalises across competitor sizes.

6. **Extract hook patterns from slide 1.** For each of the top 20, write
   down:

   - Hook archetype (cross-reference `../../shared/hook-bank-100.md`
     archetype names: Problem-Aware, Contrarian, Curiosity Gap,
     Authority, Pattern Interrupt, Specific Number, etc.)
   - Verbatim hook text
   - One-line "why it worked" hypothesis

7. **Identify 20 candidate carousel ideas for the user's brand.** Each
   candidate must:

   - Use a hook archetype that scored well in research
   - Be on-topic for the user's niche
   - Be teachable as a 5-7 slide carousel (not too thin, not too dense)
   - Avoid duplicating existing content from the user's own handle (ask
     if unsure)

8. **Voice-grade the candidate ideas through content-engine + humanizer
   BEFORE saving.** Hooks especially, they're the highest-leverage line.

9. **Write the output file.**

## Output shape

Write to `~/board/_active/content-factory-<TODAY>/01-research.md`:

```markdown
# Stage 1: Research

**Date:** <YYYY-MM-DD>
**Niche:** <niche>
**Brand handle:** <handle>
**Time window:** last <N> days
**Mode:** <live data | FIXTURE (Apify unavailable)>

## Competitor / adjacent accounts

| handle | positioning | relevance |
|---|---|---|
| ... | ... | ... |

## Top 20 trending carousels (last <N> days)

| rank | handle | hook (slide 1, verbatim) | archetype | likes | comments | saves | engagement score |
|---|---|---|---|---|---|---|---|
| 1 | ... | ... | ... | ... | ... | ... | ... |
| ... |

## Hook pattern analysis

- **Most common archetype:** <archetype> (<N>/20)
- **Highest-scoring archetype:** <archetype> (avg score <X>)
- **Underused archetype for the niche:** <archetype>

## 20 candidate carousel ideas for <brand handle>

| # | hook (draft) | archetype | template (Stage 2 will confirm) | one-line content angle |
|---|---|---|---|---|
| 1 | ... | ... | carousel-tips | ... |
| ... |

## Notes for Stage 2

- <Anything Stage 2 should know, e.g. "user has already covered topic X
  in last 30 days, deprioritise similar angles">
```

## Kill criteria

- Niche is one word → STOP, ask for ICP.
- <5 viable trending posts surfaced → STOP, ask user to narrow niche or
  supply manual references.
- Fixture mode firing for the 2nd time this session → STOP, ask user to
  check Apify connection.
- If you find yourself writing filler ("In today's fast-paced digital
  landscape...") STOP and ask the user to narrow the niche. Filler is a
  symptom of too-broad scope.

## Rejected (do not do)

- ❌ Don't fabricate competitor handles. If the user can't name them and
  you can't find them, ask.
- ❌ Don't include reels or single-image posts in the top 20.
- ❌ Don't paste verbatim hooks as candidates for the user's brand ,
  rebuild the angle, never copy.
- ❌ Don't skip the voice-grade. Hooks especially are the highest-leverage
  text in the whole pipeline.
- ❌ Don't write candidate ideas in em-dash-heavy AI prose. The
  content-engine will reject them.

## MCP / dependency calls

- `apify-content-analytics` (preferred for live data)
- `content-engine` (mandatory ship-gate)
- `humanizer` (mandatory ship-gate)
- `../../shared/hook-bank-100.md` (read-only, for archetype names)
