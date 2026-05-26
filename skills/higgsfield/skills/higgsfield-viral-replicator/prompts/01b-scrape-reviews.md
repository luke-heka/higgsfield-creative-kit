# Prompt 01b, Scrape Product Reviews

You have a G2 / Trustpilot reviews URL (or the user has pasted review
text directly). Capture up to 25 reviews and structure them for the
clustering step.

## Tool ladder (run in order, stop at first success)

### 1. Apify MCP (CANONICAL, try first)

For G2:

```
mcp__apify__search-actors with query "g2 reviews scraper"
→ pick the highest-usage actor (typically apidojo/g2-reviews-scraper or similar)
mcp__apify__fetch-actor-details with actorId "<picked>"
mcp__apify__call-actor with actorId "<picked>", input {
  "startUrls": ["<reviews URL>"],
  "maxReviews": 25,
  "proxy": { "useApifyProxy": true }
}
mcp__apify__get-dataset-items with the returned datasetId
```

For Trustpilot:

```
mcp__apify__search-actors with query "trustpilot scraper"
→ pick the highest-usage actor
mcp__apify__fetch-actor-details with actorId "<picked>"
mcp__apify__call-actor with the input schema fields filled
mcp__apify__get-dataset-items with the returned datasetId
```

If the call succeeds and returns ≥3 reviews, proceed to "Persist" step
below.

### 2. agent-browser (FALLBACK, when Apify is blocked or has no actor)

```bash
agent-browser open "<reviews URL>"
agent-browser snapshot -i
# extract each review card: reviewer name, role, company size, rating,
#   what-they-like, what-they-dislike, problems-solving
# G2 anti-bot patterns to watch for in snapshot text:
#   - "Pardon Our Interruption"
#   - "Just a moment..."
#   - "Cloudflare"
#   - "Checking your browser"
# If any of those appear → close browser, fall through to step 3.
# Otherwise scroll for more reviews:
agent-browser scroll
agent-browser snapshot -i
# Accumulate up to 25 reviews
agent-browser close
```

For Trustpilot the selectors differ but the snapshot-based extraction
is the same. Trustpilot's anti-bot is lighter than G2's.

### 3. Pasted review text (USER-PROVIDED, skip 1+2)

If the user pasted reviews directly, skip the scraper entirely. Parse
the pasted text into the same per-review schema as Apify/agent-browser
would have produced. Be permissive, pasted reviews rarely have full
metadata.

### 4. Hard fallback, fixture

If 1 and 2 both fail (Apify has no actor + agent-browser hits the
Cloudflare challenge), tell the user:

> "Both the Apify scraper and agent-browser were blocked on the live
> reviews page (typical G2 Cloudflare challenge). Running the
> clustering step on the Castos fixture from examples/. The themes
> will be plausible but won't reflect [BRAND]'s actual reviews."

Then load `examples/castos-g2-fixture.md` as the input. Tag the
`raw-reviews.json` with `"source": "fixture", "reason": "<scraper block reason>"`.

## Per-review schema (canonical)

```json
{
  "reviewer_name": "string or 'Verified User'",
  "role": "string (e.g. 'Owner, marketing agency')",
  "company_size": "Solo | Small-Business | Mid-Market | Enterprise",
  "rating": 1-5,
  "what_they_like_best": "verbatim string, DO NOT smooth grammar",
  "what_they_dislike": "verbatim string",
  "problems_solving": "verbatim string",
  "quote_excerpt": "the one pull-quote candidate from this review",
  "review_url": "deep link to the individual review if available"
}
```

## Persist

Write the array of reviews to:

`<output-folder>/raw-reviews.json`

Where `<output-folder>` is `~/board/_active/viral-replicator-<YYYY-MM-DD>/<brand>-reviews/`.

Include a top-level metadata block:

```json
{
  "brand": "<brand name>",
  "source": "apify | agent-browser | pasted | fixture",
  "source_url": "<URL or null>",
  "scraped_at": "<ISO timestamp>",
  "review_count": <int>,
  "reviews": [ ... ]
}
```

## Discipline rules

- **Verbatim quotes only.** Do not paraphrase, summarise, or "tidy"
  customer language. "It just works for me, finally" is the credibility
  signal, don't rewrite it as "It works seamlessly."
- **Attribution as full as data allows.** If only "Verified User" is
  available, that's fine. If name + role + size is available, capture
  all three.
- **Skip reviews that name competitors UNLESS the testimonial IS the
  switch.** Reviews like "way better than Buzzsprout" cluster differently
  to "I love the unlimited shows tier", the first is a switching
  testimonial, the second is a feature testimonial.
- **Capture both the like AND dislike.** Even though only the like will
  be used in the ad, the dislike is signal, if 5 reviewers cite the
  same dislike, that's a brand weakness to NOT amplify in the ad.

## What feeds this output

The next prompt (`02b-themes-from-reviews.md`) clusters these reviews
into 2-3 testimonial themes. Don't lose any structured fields, the
clustering step uses the `role` and `company_size` for "that's me too"
audience matching.
