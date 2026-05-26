# Prompt 02b, Cluster Reviews into Testimonial Themes

You have `raw-reviews.json` from prompt 01b. Cluster the reviews into
2-3 testimonial themes that can each support a 30-second ad spot.

## Step 1, Read every review

Read every review in `raw-reviews.json` (not just summaries, the
verbatim `what_they_like_best`, `what_they_dislike`, and
`problems_solving` fields). Capture the underlying customer truth, not
the feature mention.

Two reviews mentioning the SAME feature are NOT the same theme if they
value it for different reasons.

Example:

- Reviewer A: "Castos's WordPress integration is rock-solid. We run our
  whole site on WordPress and the plugin handles every edge case."
- Reviewer B: "Castos's WordPress integration meant I didn't have to
  rebuild my whole content stack to start a podcast."

Both mention "WordPress integration". Different themes:

- A's truth = "I needed it to work with the platform we live on" (technical fit)
- B's truth = "I wanted to grow without rebuilding my stack" (switching cost)

## Step 2, Name themes in customer voice

A theme name should be a CUSTOMER TRUTH, not a feature name:

| Good (customer truth) | Bad (feature name) |
|---|---|
| "I needed someone in my corner." | "Customer support." |
| "I wanted to grow without rebuilding my stack." | "WordPress integration." |
| "Don't punish me for growing." | "Unlimited pricing tier." |
| "Finally, audio AND video in one host." | "Multi-format support." |
| "My audience actually listens now." | "Private RSS feed." |

Theme name format: short sentence in quotes, customer voice, first
person where possible.

## Step 3, Cap at 3 themes

If you find more than 3, the top 3 by frequency win. Note the rest as
"themes we cut" at the bottom, don't dilute the ad scripts by
spreading thin.

For each theme:

- **Theme name** (verbatim customer voice, in quotes)
- **Customer truth** (1 sentence, what the customer is actually
  feeling/needing/escaping)
- **Why this theme converts** (1 sentence, what about this maps to a
  viewer's "that's me too" reaction)
- **Pull-quote (verbatim)** with reviewer attribution (name or "Verified
  User" + role + company size)
- **Supporting quotes (2-3)** verbatim from other reviews in the same
  theme cluster
- **Avoid quoting** note for any too-vague reviews in this theme (e.g.
  "works great!" is too vague to anchor a 30s ad)

## Output schema

```
# Testimonial Themes, <brand>

**Source:** <reviews URL or "pasted" or "fixture">
**Review count analysed:** <int>
**Themes shipped:** <int, usually 2-3>

---

## Theme 1, "<theme name in customer voice>"

**Customer truth:** 1 sentence
**Why this theme converts:** 1 sentence
**Frequency in review set:** <N of <total> reviews>

**Pull-quote (verbatim):**

> "<exact quote from a review, DO NOT smooth grammar>"
>
>, <Reviewer name or "Verified User">, <Role>, <Company size>

**Supporting quotes (verbatim):**

> "<quote 2>"
>
>, <Reviewer 2 attribution>

> "<quote 3>"
>
>, <Reviewer 3 attribution>

**Avoid quoting in this theme:**
- (any review that's too vague, list reviewer attribution + reason)

---

## Theme 2, "<theme name>"

(same shape)

---

## Theme 3, "<theme name>"

(same shape, only if 3 themes warrant it)

---

## Themes we cut

- "<theme name>", 1-line reason for cutting (e.g. "only 2 reviews
  mentioned it, not enough frequency for a 30s ad")
- "<theme name>", 1-line reason
```

## Quote selection rules (HARD)

- **Pull verbatim.** Don't smooth grammar. "It just works for me,
  finally" is more credible than "It works seamlessly."
- **One sentence pull-quote, two max.** Long quotes don't fit on
  screen (text-on-broll treatment) and don't deliver as VO (talking-head
  treatment).
- **Attribute as fully as the data allows.** Name + role + company size
  if available. "Verified User" + role if not. Never invent attribution.
- **Avoid quotes that name competitors UNLESS the testimonial IS the
  switch.** "Way better than Buzzsprout" is fine if the theme is a
  switching testimonial. Otherwise it pulls focus from the brand.
- **The pull-quote must work as a 0-3s HOOK.** If the quote doesn't
  grab attention in the first 3 seconds of an ad, swap it for one that
  does. Look in the supporting quotes for a better hook candidate.

## Selr AI brand bonus step (only if brand is Selr AI)

If the brand being analysed is Selr AI, attempt to match each pull-quote
to a GHL contact:

1. Search GHL contacts by reviewer name + company (if both available)
2. If matched, create a Notion entry tagged with the contact for source
   of truth
3. Note the match status in the theme block:
   `**GHL match:** matched | unmatched | not attempted`

Skip this for any other brand, it's Selr-specific.

## Output destination

Write to: `<output-folder>/themes.md`

Where `<output-folder>` is `~/board/_active/viral-replicator-<YYYY-MM-DD>/<brand>-reviews/`.

Then run prompt `03b-testimonial-ad-treatment.md` to pick the visual
treatment per theme.

## What feeds this output

The next prompt picks ONE visual treatment per theme (A talking-head /
B text-on-broll / C side-by-side) and writes the Higgsfield prompt +
30s ad script for each.
