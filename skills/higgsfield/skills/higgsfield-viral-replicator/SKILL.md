---
name: higgsfield-viral-replicator
description: >
  Use when the user wants to either (a) deconstruct a viral
  Instagram/TikTok/YouTube Short and rebuild it for their brand, or
  (b) scrape product reviews from G2/Trustpilot and turn them into a
  testimonial-style video ad. Two-path skill, Path A is "deconstruct
  this viral video / rebuild this for my brand", Path B is "scrape
  these reviews into a testimonial ad / turn G2 reviews into a video".
  Both paths produce a paste-ready Higgsfield video prompt and hand
  off to cinematic-ai-reels or motion-graphic-reels for final
  assembly. Triggers on "deconstruct this viral video", "rebuild this
  for my brand", "scrape these reviews into a testimonial ad", "turn
  G2 reviews into a video", "make a version of this reel for [brand]".
  Does NOT trigger on pure analytics asks (those route to
  apify-content-analytics) or on rebuild-assembly asks (those route
  to cinematic-ai-reels or motion-graphic-reels directly).
user-invocable: true
metadata:
  tags: [higgsfield, viral, deconstruct, rebuild, testimonial, reviews, g2, trustpilot, instagram, tiktok, youtube, reel, ad]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
  pairs_with:
    - apify-content-analytics (canonical scraping engine, IG/TikTok/YT-Shorts/G2/Trustpilot)
    - agent-browser (fallback scraping engine when Apify is blocked or rate-limited)
    - reels-hook-score (rank viral references by hook strength)
    - cinematic-ai-reels (rebuild dispatcher option A, AI-B-roll mix, TODO when cinematic-ai-reels ships, currently falls back to motion-graphic-reels or frontcam-reels)
    - motion-graphic-reels (rebuild dispatcher option B, Greg-style motion graphics)
    - frontcam-reels (rebuild dispatcher fallback when cinematic-ai-reels is not yet installed)
    - notebook-reels (rebuild dispatcher fallback for AI-narration formats)
    - content-engine (voice ship-gate, MANDATORY)
    - humanizer (slop ship-gate, MANDATORY)
    - higgsfield-recipes (genre template match)
    - higgsfield-prompt (rebuild prompt construction)
---

# Higgsfield Viral Replicator + Review-to-Ad

## What this is, in plain English

**One-liner:** Two ways to turn other people's wins into your own ads, paste a viral video URL and the skill figures out why it worked then rebuilds it for your brand, OR paste a reviews page (G2, Trustpilot) and it turns the real customer quotes into testimonial-style video ads.

**Use it when you want to:**
- Copy the structure of a viral reel without copying the content
- Find out why someone else's reel went viral and apply the same trick to yours
- Turn 5-star reviews into an ad nobody else has, using verbatim customer words
- Produce a testimonial ad without filming real customers

**Don't use it for:**
- Pure engagement analytics on viral references (use `apify-content-analytics`)
- Final assembly of the rebuilt reel into a finished video (this skill hands off to `motion-graphic-reels`, `cinematic-ai-reels` (when installed), `frontcam-reels`, or `notebook-reels`)

**Roughly:**
- $1 to $5 per deconstruction + rebuild (Apify scrape + one Higgsfield 5-8s hero shot), $2 to $8 per testimonial-theme set (review scrape + hero shot)
- 5 to 15 minutes per run end-to-end (longer if downstream reel skill renders the full cut)
- You get, a deconstruction or themes file, a paste-ready Higgsfield prompt, and a hand-off note pointing the next reel skill to load

**Inputs you'll need:**
- Path A, a viral video URL (Instagram, TikTok, or YouTube Shorts) plus a one-sentence brand context
- Path B, a G2 or Trustpilot reviews page URL OR pasted review text (2 or more reviews)
- Your brand voice (auto-loaded from memory for Selr AI, ask once for any other brand)

---

Two paths, same destination. Either deconstruct a viral video and rebuild
it for the user's brand, or turn product reviews into a testimonial ad.
Both paths terminate in a paste-ready Higgsfield prompt plus a hand-off
to the appropriate Selr AI reel assembly skill.

This is the MOST GREEN-FIELD of the planned Higgsfield sub-skills,
nothing else in Luke's stack does deconstruct-then-rebuild or
reviews-to-video-script.

---

## When This Skill Triggers

Trigger phrases (route here):

- "Deconstruct this viral video and rebuild it for [brand]"
- "What made this Reel work? Now make me a version for my brand"
- "Make a version of this TikTok for [brand]"
- "Pull G2 reviews from [URL] and turn them into a testimonial ad"
- "Scrape Trustpilot reviews for [brand] and write me 3 ad scripts"
- "Turn these reviews into a testimonial video"

Do NOT trigger on:

- "Analyse the engagement on this post" → routes to `apify-content-analytics`
- "Assemble this reel script" / "render this reel" → routes to
  `cinematic-ai-reels` or `motion-graphic-reels` directly
- "Write me a carousel from this idea" → routes to `higgsfield-content-factory`

---

## Routing Table (run on first user input)

| User input contains | Path |
|---|---|
| `instagram.com/reel/*` or `instagram.com/p/*` | **A** (viral deconstruction) |
| `tiktok.com/@*/video/*` | **A** |
| `youtube.com/shorts/*` | **A** |
| `g2.com/products/*/reviews` | **B** (reviews-to-ad) |
| `trustpilot.com/review/*` | **B** |
| Pasted review text without URL | **B** |
| Both (URL + reviews) | Run **A** first, then ask whether to also run **B** |

If the input is ambiguous (e.g. a plain text idea with no URL and no
quotes), ask once: "Is this (a) a viral video to deconstruct, or (b)
customer reviews to turn into an ad?" Then route. Do not guess.

---

## Output Destination

All runs write to `~/board/_active/viral-replicator-<YYYY-MM-DD>/<source-slug>/`.

- Path A folder name: `<creator-handle>-<post-id>/`
  (e.g. `kallaway-DAi1lWIPFuB/`)
- Path B folder name: `<brand>-reviews/`
  (e.g. `castos-reviews/`)

Inside each folder, depending on the path:

```
~/board/_active/viral-replicator-2026-05-24/
├── kallaway-DAi1lWIPFuB/        (Path A)
│   ├── raw-post.json
│   ├── deconstruction.md
│   ├── rebuild.md
│   ├── higgsfield.md
│   └── handoff.md
└── castos-reviews/              (Path B)
    ├── raw-reviews.json
    ├── themes.md
    ├── treatment.md
    ├── higgsfield.md
    └── handoff.md
```

After a run, also append a one-line entry to `~/board/_log.md`:

```
- viral-replicator: deconstructed @kallaway DAi1lWIPFuB, rebuilt for Selr AI (handoff → motion-graphic-reels) (2026-05-24)
```

---

## Path A, Viral Replication

### Step 1, Fetch the post

**Default tool: Apify MCP (most reliable, no anti-bot maintenance).**

For Instagram URLs, prefer Apify's `mcp__apify__apify--instagram-post-scraper`
actor. It returns clean structured JSON with caption, hashtags, view count,
like count, comment count, video URL, thumbnail URL, dimensions.

Pattern:

```
1. Search for the actor (if first run): mcp__apify__search-actors with query "instagram post scraper"
2. Inspect input schema: mcp__apify__fetch-actor-details with actorId "apify/instagram-post-scraper"
3. Run it: mcp__apify__call-actor with actorId "apify/instagram-post-scraper",
   input { "directUrls": ["<URL>"], "resultsLimit": 1 }
4. Pull results: mcp__apify__get-dataset-items with the returned datasetId
5. Persist raw JSON to raw-post.json in the output folder.
```

For TikTok URLs, use `mcp__apify__clockworks--tiktok-scraper` (per-post mode)
or `mcp__apify__clockworks--tiktok-video-scraper`.

For YouTube Shorts URLs, prefer `mcp__apify__streamers--youtube-scraper`.

**Fallback: `agent-browser` (when Apify is rate-limited or returns 403).**

Apify is the CANONICAL path. `agent-browser` is the fallback when Apify
exhausts quota or hits anti-bot for that specific post.

Pattern:

```bash
agent-browser open "<URL>"
agent-browser snapshot -i
# pull caption, on-screen text, video thumbnail from the snapshot refs
agent-browser screenshot --out raw-post-cover.jpg
agent-browser close
```

Capture the same fields Apify returns: caption, hashtags, on-screen text
visible in the cover frame, video thumbnail, duration, engagement counts
(visible or scraped from page meta).

**Hard fallback: deterministic fixture (when both scrapers are blocked).**

If Apify returns empty AND `agent-browser` is rate-limited (the Instagram
login wall is the usual culprit), load `examples/kallaway-fixture.md` as
the deconstruction input and tell the user explicitly: "Both the Apify
scraper and agent-browser were blocked on the live post. Running the
deconstruction on the Kallaway fixture so the demo completes. The
rebuild will still be brand-correct because it uses the deconstruction
output, not the raw post."

Write the source-of-truth note to `raw-post.json` even when using the
fixture, with `"source": "fixture", "reason": "<scraper block reason>"`
fields so downstream skills know.

### Step 2, Deconstruct

Load `prompts/01a-deconstruct-viral.md`. Produce a 9-section structured
breakdown using the `templates/deconstruction.md` schema. The 9 sections
are:

1. **Hook archetype** (which of the 10 hook archetypes from
   `../shared/hook-bank-100.md`, problem-aware, contrarian,
   curiosity-gap, specific-number, story-in-1-sentence, named-character,
   visual-mismatch, claim-then-prove, stat-drop, question-implying-contrarian-answer)
2. **Pattern interrupts** (enumerate every cut, zoom, scale change,
   sound shift, on-screen text change, framing shift)
3. **Narrative arc** (3-5 beats, what changes for the viewer's
   understanding or emotion, NOT a play-by-play)
4. **Visual style** (subject framing, camera energy, color & light,
   cut frequency, style references)
5. **Audio role** (music, VO, diegetic sound, audio's specific job)
6. **Payoff** (what the viewer gets in the last 3s, payoff shape,
   why it's emotionally satisfying for this audience)
7. **CTA mechanism** (explicit CTA verbatim if present, implicit
   behaviour the video is engineering)
8. **Why-it-went-viral hypothesis** (2-3 sentences naming specific
   mechanics, identity-confirmation, status-transfer, curiosity-gap,
   visual-novelty, comment-bait)
9. **What's NOT replicable** (the parts that depend on the original
   creator's identity, audience, or moment, explicitly the parts
   you should NOT copy in the rebuild)

Write to `deconstruction.md`.

**Discipline:**

- Don't praise the video. Diagnose it.
- "It's just well-edited" is not a deconstruction. Name the specific
  edit choices.
- If you're stuck on "why it worked", read what the COMMENTS would say
 , that's usually the answer.

### Step 3, Rank by hook strength (optional but recommended)

If the user provided multiple viral references in one ask, pipe the
deconstructions through `reels-hook-score` to rank them. Rebuild from
the top-scored reference, document the others in `deconstruction.md`
as a "considered but not rebuilt" list.

For a single reference, skip this step.

### Step 4, Rebuild for the user's brand

Ask once (if not provided): "What's the brand and topic this rebuild
is for? One sentence."

Defaults if the brand is Selr AI:

- Load Selr AI voice from `~/.claude/projects/-Users-luke/memory/selrai-business-model.md`
- Load Selr AI URLs from `~/.claude/projects/-Users-luke/memory/brand-contact-urls.md`
- Apply the no-em-dash, no-outcome-guarantee, no-support-promise rules
  automatically

Load `prompts/02a-rebuild-viral.md` and produce:

- A shot-by-shot script (table format, see `templates/rebuild-prompt-skeleton.md`)
- A paste-ready Higgsfield video prompt for the dominant shot only
  (Higgsfield is best at single-action 5-8s clips, render the
  dominant shot, document the full cut sequence in the table)
- A caption draft (≤200 chars before the cutoff, then expansion, in
  the user's brand voice, NOT the original creator's voice)

Use `../shared/higgsfield-prompt-skeletons.md` Skeleton 4 as the
canonical structure for the Higgsfield prompt.

Write to `rebuild.md` and `higgsfield.md`.

**Rebuild rules:**

- **Keep:** hook archetype, pattern-interrupt cadence, payoff shape, CTA mechanic
- **Change:** subject, setting, voice, specific words, music
- **Never copy verbatim:** captions, on-screen lines, phrasings, paraphrase the structure, write fresh language
- **One mechanic per rebuild.** If the original stacked 3 mechanics, pick the one that maps cleanest to the user's brand
- **Resist on-the-nose.** Sushi-chef original → don't rebuild as "insulated-cup chef". Translate the mechanic to the brand's actual world

### Step 5, Voice ship-gate (MANDATORY)

Every text output from steps 2-4, deconstruction notes, rebuilt script,
caption, on-screen captions, MUST pipe through:

1. `content-engine` (voice fingerprint + slop blocklist + 5-axis critic)
2. `humanizer` (Wikipedia signs-of-AI-writing rewriter)

If either gate fails, rewrite the failing lines and re-run. Do not ship
text that hasn't passed both gates.

### Step 6, Hand off to the right reel skill

Load `prompts/03a-handoff-to-reel-skill.md`. Apply the dispatcher rule
based on the deconstruction's "Visual style" + "Audio role" sections:

| Original archetype | Hand off to |
|---|---|
| Talking-head with cuts + warm grade + voice carries (Kallaway, Hormozi, Iman Gadzhi style) | `cinematic-ai-reels` (real VO + AI B-roll mix). FALLBACK if not installed, `frontcam-reels` for real-VO talking-head, OR `motion-graphic-reels` with a note in handoff.md |
| 100% motion-graphic with Fraunces/typeset text + named visual primitives (Greg Isenberg style, Jay Clouse style, Daniel Stojnic style) | `motion-graphic-reels` (Greg-style with locked Selr palette) |
| Mixed (real talking-head + motion-graphic overlays) | `cinematic-ai-reels` as primary, with motion-graphic-reels primitives layered. FALLBACK if not installed, `frontcam-reels` for the talking-head layer + `motion-graphic-reels` for overlays |
| AI-narration / faceless-voice over visuals (NotebookLM-style) | `notebook-reels` |
| Pure UGC product unboxing / user-generated | Pre-empt, note in `handoff.md` that this should route to `higgsfield-ugc-ads` instead, do not run the rebuild here |

**Fallback rule when `cinematic-ai-reels` is not installed:** check `ls ~/.claude/skills/` first. If absent, pick the closest installed sibling per the rows above and write the deviation explicitly into `handoff.md` so the user knows why the route was changed. TODO when cinematic-ai-reels ships, remove the fallback rows.

Write the hand-off note to `handoff.md` including:

- Which reel skill to load next
- The deconstruction file path
- The rebuild file path
- The Higgsfield prompt file path
- Any deviations from the default reel skill flow that this rebuild needs

The user then explicitly invokes the next skill (e.g. "now run
motion-graphic-reels on this hand-off"). This skill does NOT auto-fire
the downstream skill, the hand-off is a deliberate boundary.

### Step 7, Render (optional)

If the user wants to preview the dominant shot before handing off, call
the Higgsfield MCP via runtime ToolSearch. Do not hard-code Higgsfield
tool names, they evolve. Pattern:

```
ToolSearch with query "higgsfield video"
pick the matching tool (most likely a text-to-video or image-to-video)
call it with the prompt from higgsfield.md
```

If MCP isn't connected, the prompt sits paste-ready in `higgsfield.md`.

---

## Path B, Review-to-Ad

### Step 1, Scrape reviews

**Default tool: Apify MCP.**

For G2, search for an actor with `mcp__apify__search-actors` query
"g2 reviews scraper". Pick the highest-usage actor. Inspect its input
schema with `mcp__apify__fetch-actor-details`. Run it with the reviews
URL and a `maxReviews: 25` cap. Pull results via
`mcp__apify__get-dataset-items`.

For Trustpilot, search query "trustpilot scraper". Same pattern.

For pasted review text (no URL), skip this step entirely.

**Fallback: `agent-browser`.**

If Apify has no usable actor for the platform or hits a paywall, use
`agent-browser`:

```bash
agent-browser open "<reviews URL>"
agent-browser snapshot -i
# extract review cards from the snapshot, each card has reviewer
# name/role/size, rating, what-they-like, what-they-dislike, quote
# scroll for more if needed: agent-browser scroll
# repeat snapshot, accumulate up to 25 reviews
agent-browser close
```

**Hard fallback: fixture.**

If both Apify and `agent-browser` are blocked (G2 is aggressive about
this, Cloudflare challenge is common), load `examples/castos-g2-fixture.md`
and tell the user explicitly. Set `"source": "fixture"` in `raw-reviews.json`.

Per-review schema:

```json
{
  "reviewer_name": "string or 'Verified User'",
  "role": "string",
  "company_size": "Solo | Small-Business | Mid-Market | Enterprise",
  "rating": 1-5,
  "what_they_like_best": "verbatim string",
  "what_they_dislike": "verbatim string",
  "problems_solving": "verbatim string",
  "quote_excerpt": "the one pull-quote candidate"
}
```

Write to `raw-reviews.json`.

### Step 2, Cluster into testimonial themes

Load `prompts/02b-themes-from-reviews.md`. Produce 2-3 testimonial
themes using the rule: theme name = customer truth, NOT feature name.

Good: "I needed someone in my corner."
Bad: "Customer support."

Good: "I wanted to grow without rebuilding my stack."
Bad: "WordPress integration."

For each theme:

- Theme name (verbatim customer voice, in quotes)
- Customer truth (1 sentence, what the customer is actually
  feeling/needing/escaping)
- Why this theme converts (1 sentence, what about this maps to a
  viewer's "that's me too" reaction)
- Pull-quote (verbatim, with reviewer attribution, name or "Verified
  User" + role + company size)
- Supporting quotes (2-3 verbatim quotes from other reviews in the
  same theme cluster)
- "Avoid quoting" note for any too-vague reviews in this theme

Cap at 3 themes. If more emerge, top 3 by frequency win. Note the cut
themes at the bottom as a "themes we cut" line, don't dilute the ad
scripts.

**Customer-quote sanctity:**

- Pull verbatim. Don't smooth grammar.
- "It just works for me, finally" beats "It works seamlessly."
- One sentence pull-quote, two max, long quotes don't fit on screen.
- Avoid quotes that name competitors unless the switch IS the testimonial.

**Optional GHL/Notion tagging (Selr AI brand only):**

If the brand being scraped IS Selr AI, attempt to match each verbatim
quote to a GHL contact (search by reviewer name + company). If matched,
create a Notion entry tagged with the contact for the source of truth.
Skip this for any other brand.

Write to `themes.md`.

### Step 3, Pick treatment per theme

Load `prompts/03b-testimonial-ad-treatment.md`. For each theme, pick
ONE of the three treatments. Don't blend.

| Theme character | Treatment |
|---|---|
| Emotional / "this saved my business" / founder accessibility | **A, Talking-head reconstruction** |
| Technical / specific-feature / measurable savings | **B, Text-on-b-roll with VO** |
| Migration / "I switched FROM" / before-after comparison | **C, Side-by-side before/after** |

Use `templates/testimonial-treatment.md` for the field-by-field schema,
and `../shared/higgsfield-prompt-skeletons.md` Skeleton 5 for the
Higgsfield prompt construction.

**Disclosure rule (MANDATORY for treatment A):**

Every AI-rendered customer face MUST display on-screen text:
"Represents a customer profile, not a specific person."

Small bottom-corner placement, lower-third, not over the face. Stays
on-screen for the full duration of the talking-head shot. This is
non-negotiable, both for ethics and for ad-platform compliance.

Document the disclosure in the deliverable, in `treatment.md` itself,
and inside the Higgsfield prompt's brand-visibility block.

### Step 4, Build the 30-second ad spot

For each chosen theme + treatment, write a 30-second testimonial spot:

- **Hook (0-3s):** uses the pull-quote or a paraphrase of the hook line
- **Setup (3-10s):** sketch the customer's "before" world
- **Demonstration (10-22s):** show or imply the product solving the truth
- **Payoff + CTA (22-30s):** quote the resolution line + soft CTA

Higgsfield generates the visual hero shot or B-roll cut for the spot
(5-8s segment). The full 30s ad is assembled in the downstream reel
skill, Higgsfield does not render 30s clips reliably.

Write the script + the Higgsfield prompt to `treatment.md` and
`higgsfield.md`.

### Step 5, Voice ship-gate (MANDATORY)

Same as Path A step 5. Every text output from steps 2-4, themes,
treatments, captions, on-screen text, VO scripts, pipes through
`content-engine` + `humanizer`. No exceptions.

### Step 6, Hand off to the right reel skill

Load `prompts/03a-handoff-to-reel-skill.md`. Apply the dispatcher rule:

| Treatment | Hand off to |
|---|---|
| A, Talking-head reconstruction | `cinematic-ai-reels` (AI talking head IS a real-feeling face, needs the cinematic stack's color grade + audio polish). FALLBACK if not installed, `frontcam-reels` with a note in handoff.md that the cinematic-grade pass needs to be done manually until `cinematic-ai-reels` ships |
| B, Text-on-b-roll with VO | `motion-graphic-reels` (text-on-screen is the motion-graphic primitive's job) |
| C, Side-by-side before/after | `motion-graphic-reels` (split-screen + label primitives are motion-graphic territory) |

**Fallback rule:** same as Path A step 6. If `cinematic-ai-reels` is not installed, route to `frontcam-reels` and document the deviation in `handoff.md`. TODO when cinematic-ai-reels ships, remove this fallback row.

Write the hand-off note to `handoff.md`. Same shape as Path A step 6.

### Step 7, Render (optional)

Same MCP pattern as Path A step 7.

---

## Reverse Lookup, When to NOT Use This Skill

This skill does NOT poach the following adjacent skills' territory:

| User intent | Correct skill | Why not this one |
|---|---|---|
| "What's the engagement on this post?" | `apify-content-analytics` | That's pure analytics, no rebuild. |
| "Assemble these chunks into a finished reel" | `cinematic-ai-reels` or `motion-graphic-reels` | That's the assembly layer, this is the structural layer. |
| "Generate a UGC product ad for [SKU]" | `higgsfield-ugc-ads` | Pure-UGC has its own treatment lib. |
| "Build me a 7-slide carousel teaching X" | `higgsfield-content-factory` | Wrong output format. |
| "Write me Facebook ad copy variations" | `ad-creative` | Pure copy, no video. |

If a user asks for something on this table, route them to the correct
skill instead of running.

---

## Voice + Style Constraints (Selr AI House Rules, Apply to ALL Outputs)

These are enforced by `content-engine` + `humanizer` in step 5, but
should also be applied at draft time to reduce iteration:

- **No em dashes.** Use commas, full stops, or colons.
- **AU English.** Colour not color, organise not organize, optimise not optimize.
- **Banned vocab:** "game-changer", "10x", "crushing it", "killing it",
  "secret sauce", "level up", "unlock", "transform", "revolutionise",
  "elevate", "supercharge", "next-level", "best-in-class", "world-class".
- **No outcome guarantees.** No "you will get X result", use process
  language ("walk through how to install", "see how it runs").
- **No support promises in marketing.** No "weekly Q&A", "office hours",
  "ongoing helpdesk" in any caption or on-screen text.
- **No refund / money-back promises** anywhere.
- **No personal-life mixing** for Selr AI brand outputs, business
  context only.
- **Customer quotes verbatim**, never paraphrase, never polish grammar.
- **Disclosure for AI-rendered faces:** "Represents a customer profile,
  not a specific person", on-screen, every time, treatment A.

---

## Quick Demos

```
Deconstruct https://www.instagram.com/p/DAi1lWIPFuB/ and rebuild it
for Selr AI's workshop offer.
```

```
Scrape https://www.g2.com/products/castos/reviews and turn them into
3 testimonial ad treatments. Hand off to motion-graphic-reels.
```

```
Here's a TikTok URL https://www.tiktok.com/@gregisenberg/video/...
and my brand is "an AI-ops consultancy for solo PTs". Build the
rebuild and route through cinematic-ai-reels.
```

```
Take these 12 pasted reviews [...] and build me one talking-head
testimonial ad on the "I needed someone in my corner" theme.
```

---

## See Also

- `../shared/higgsfield-prompt-skeletons.md` (Skeleton 4 = rebuild
  canonical, Skeleton 5 = testimonial three-treatment canonical)
- `../shared/hook-bank-100.md` (10 hook archetypes for the
  deconstruction step)
- `../shared/capcut-finishing.md` (post-production fixes for
  multi-chunk assembly, applied in the downstream reel skill, not here)
- `~/.claude/skills/motion-graphic-reels/SKILL.md` (one of the two
  downstream assembly skills)
- `~/.claude/skills/cinematic-ai-reels/SKILL.md` (the other downstream
  assembly skill, if not yet installed, fall back to
  `motion-graphic-reels` and document the deviation)
- `~/.claude/skills/apify-content-analytics/SKILL.md` (sister skill
  for pure analytics, NOT for rebuild)
- `~/.claude/skills/reels-hook-score/SKILL.md` (optional ranking step)
