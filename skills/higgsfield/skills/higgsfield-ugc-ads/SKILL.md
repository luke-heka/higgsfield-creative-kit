---
name: higgsfield-ugc-ads
description: >
  Use when the user wants a multi-chunk UGC product ad built end-to-end in
  Higgsfield Seedance 2.0 with character lock across chunks, an `@product`
  Element tag, and a CapCut assembly recipe. Triggers on "make me a UGC ad",
  "build me a multi-chunk product ad", "higgsfield UGC pipeline", "talking-head
  product video for my brand", "Alex-Robinson-style UGC ad", "product URL to
  finished ad in Higgsfield", "founder talking-head ad", "Seedance multi-chunk
  ad with consistent character". Does NOT poach `ad-creative` (copy-only
  variations) or `seedance-pipeline` (single-clip generation), this skill is
  the multi-chunk orchestrator that composes both.
user-invocable: true
metadata:
  tags: [higgsfield, ugc, ads, seedance, multi-chunk, character-lock, element-tag, product, talking-head, marketing-studio]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
---

# Higgsfield UGC Ads

## What this is, in plain English

**One-liner:** Turns your product into a short Instagram or TikTok ad that looks like a real person talking to camera, broken into bite-sized clips so each one is easy to fix without re-rendering the whole thing.

**Use it when you want to:**
- Post a product ad without filming yourself.
- Test 5 different opening hooks (the first 3 seconds) on the same product without building 5 separate ads.
- Produce a 30 to 60 second UGC-style ad (looks like a real customer talking) in under an hour.
- Create ads for a product you don't have on hand yet (works from a product photo or product URL).

**Don't use it for:**
- A one-off 5 to 10 second single-clip product video. Use `seedance-pipeline` instead.
- A paste-product-URL-and-go single ad with no script control. Use `higgsfield-marketing-studio` instead.

**Roughly:**
- ~28 credits per ad (1.5x buffer ~42 credits) for the actual render. Plus plan is the minimum ($39/mo annual, 1,000 credits/mo, 6 video / 8 image parallel). Ultra plan ($99/mo annual, 3,000 credits/mo) unlocks 8/8 parallel and 365-day UNLIMITED Nano Banana Pro, so the product still in Phase 1 is essentially free on Ultra.
- 60 to 90 minutes from product image to finished MP4 on a clean run.
- You get a finished 9:16 MP4 you can post, the caption + on-screen text + CTA copy run through the voice gate, and a per-chunk cost + credit log in the output folder.

**Inputs you'll need:**
- A product photo OR a product URL (the skill cleans the photo for you if needed).
- One sentence on what the product does and who it's for (the buyer in plain English).
- Optional: a specific person you want as the on-screen presenter (named Higgsfield avatar, your own Soul ID, or a one-off generated character).

## Starter packs

Three preconfigured business-owner packs ship with this skill. Pick your industry, fill the multi-chunk-script variables, render:

- [`starter-packs/dtc-ecommerce/`](starter-packs/dtc-ecommerce/), DTC product UGC ad, bathroom/kitchen avatar, no medical claims.
- [`starter-packs/personal-trainer/`](starter-packs/personal-trainer/), solo PT or gym owner UGC, gym-floor `@trainer` tag, no weight-loss numbers. AU.
- [`starter-packs/local-service-trade/`](starter-packs/local-service-trade/), plumber/electrician/cafe/hairdresser UGC, owner-on-site avatar. AU.

See [`../STARTER-PACKS.md`](../STARTER-PACKS.md) for the full index of 18 packs.

---

Multi-chunk UGC ad pipeline. Product URL + brand brief → a chunked script with
character lock + `@product` Element tag + per-chunk direction blocks → render
each chunk through Seedance 2.0 → assemble in CapCut → ship.

This skill is the **multi-chunk orchestrator** for the Alex-Robinson UGC pattern
(Py47FzLdF9E) combined with the Edmund-Yong two-chat hook pattern (xyKxB8q7wQk).
It does not replace `seedance-pipeline` (single-clip) or `ad-creative`
(copy-only). It composes them, plus `higgsfield-soul`, `higgsfield-audio`, and
`selrai-ad-image`, into a finished UGC ad you can post.

---

## When to use this skill

Use this when ALL of the following are true:

- The deliverable is a **product UGC ad** (founder talking-head, unboxing,
  demo, problem-solution, before-after), not a cinematic short, not a
  motion-graphic explainer.
- You need **character consistency** across more than one clip (a single
  presenter appears in multiple scenes).
- You need **product consistency** across more than one clip (the same bottle,
  app screen, device, package recurs).
- The final runtime is **15s to 60s** and naturally splits into 3–7 chunks.
- You are willing to **assemble in CapCut** at the end (this skill does not
  auto-edit, that is `hyperframes`' job).

If any of those are false, route elsewhere, see "Don't use this skill for"
below.

---

## Don't use this skill for

| Situation | Use this instead |
|-----------|------------------|
| Single-clip 5–10s product video | `seedance-pipeline` directly |
| Copy variations only (no video) | `ad-creative` |
| One image ad (square IG ad for a plumber etc) | `selrai-ad-image` |
| Cinematic AI reel with your own real voiceover | `cinematic-ai-reels` (fallback: `notebook-reels` if not installed) |
| Greg-Isenberg motion-graphic explainer reel | `motion-graphic-reels` |
| SaaS feature explainer with kinetic typography | `motion-graphic-reels` (HIGGSFIELD path) |
| Front-cam talking-head edit (no AI generation) | `frontcam-reels` |
| Cut silence + add captions on a finished video | `hyperframes` |
| One-prompt-to-campaign across image + reel + carousel + copy | `higgsfield-marketing-studio` (sibling skill) |
| Critique an already-rendered UGC ad frame-by-frame | `higgsfield-ad-critic` (sibling skill, the third chat in the loop) |

---

## The two-chat pattern (with critique = three chats)

From xyKxB8q7wQk (Edmund Yong) and Py47FzLdF9E (Alex Robinson).

Multi-chunk UGC ads break under context pressure when one chat tries to do
everything. The pattern that works is:

| Chat | Job | Inputs | Outputs |
|------|-----|--------|---------|
| **Chat 1, Hook brainstorm** | Generate 5 hook variations the presenter could open with. Ask clarifying questions BEFORE generating. | Product URL, optional brand brief, optional target audience. | 5 hook lines + pick one. Hand the chosen hook into Chat 2. |
| **Chat 2, Production** | Build the multi-chunk script. Generate each chunk's Seedance prompt. Loop until each chunk renders cleanly. | Chosen hook from Chat 1, character lock spec, product still image (from `selrai-ad-image` or Nano Banana 2), voice choice. | Multi-chunk YAML + per-chunk paste-ready Seedance prompts + downloaded clips. |
| **Chat 3, Critique loop** | Hand the assembled cut to `higgsfield-ad-critic` for frame-by-frame Gemini analysis. Apply suggestions, regenerate offending chunks. | Final CapCut export (or per-chunk MP4s). | Critique report + revised chunks. Loop until the critic gives green light. |

Each chat keeps its context clean. Chat 2 never burns hook-brainstorm tokens.
Chat 3 never burns production tokens. This is non-negotiable for a 5+ chunk ad
,  a single chat that does all three runs out of context before chunk 4.

---

## End-to-end workflow

### Phase 0: Confirm before building

Before any credits get burned, restate the intent and ask clarifying questions.
This matches `higgsfield-recall`'s confirm-first pattern.

Surface to the user:

- "I'm about to build a multi-chunk UGC ad for **[product name]**. Confirm:"
  - Product URL: `[URL]`
  - Total runtime target: `[15s / 30s / 45s / 60s]`
  - Number of chunks: `[N]` (default: 5, hook / problem / solution / proof / CTA)
  - Character: `[upload, Higgsfield avatar name, or Soul ID]`
  - Voice: `[Higgsfield Change Voice name, e.g. Megan]`
  - Framework: `[mid-funnel punchy | full-stack education]` (default: mid-funnel)
- "Should I also pull copy variations from `ad-creative` for the final CTA card?"
- "Should I run the rendered ad through `higgsfield-ad-critic` automatically when done?"

Wait for confirmation. Cost of skipping this phase is 1.5–3× credit overspend
on regenerations.

---

### Phase 1: Pre-mint product still (BEFORE any video)

Reference-first generation (pattern #4 from the transcripts report).

The `@product` Element tag in Higgsfield needs a clean source image. You have
two paths:

1. **You already have a clean product photo** → upload directly to Higgsfield
   → Elements → tag as `@product`.
2. **You only have the product URL or a messy photo** → invoke `selrai-ad-image`
   to generate a clean product render (white BG or contextual scene) → upload
   to Higgsfield → Elements → tag as `@product`.

For complex products (capsule with visible pills inside, packaging with
illegible logo), use Nano Banana 2 directly with this exact pattern (from
Py47FzLdF9E):

```
Generate a high quality render of this image against a white background and
remove the [unwanted element]. Keep the [hero element] sharp and centered.
```

Save the still to `~/board/_active/ugc-ads-<YYYY-MM-DD>/00-product-still.png`.

Do NOT proceed to video generation until the Element tag is set in
Higgsfield. The character-lock + product-lock combo is the single biggest
quality lever, half the AI-look complaints come from people who skipped this.

---

### Phase 2: Character lock (BEFORE any video)

Three paths for the character. Pick one and document it in the YAML.

| Path | When to use | How |
|------|-------------|-----|
| **Higgsfield avatar by name** | Lowest skill barrier. You want speed not specificity. | Pick a named avatar (e.g. Megan, Daniel). Soul-lock not required. Document the name in `character_lock.appearance`. |
| **Custom Soul ID** | Recurring character across campaigns. You need brand-owned identity. | Use `higgsfield-soul` to create the Soul ID from a reference image. Document the Soul ID + reference image path. |
| **One-off generated UGC presenter** | One ad, no campaign reuse. | Use GPT Image 2.0 with this exact pattern from Py47FzLdF9E: `Generate a candid and natural photo of an [attractive woman in her early 40s / authoritative man in his late 30s / whoever fits the ICP] standing in their [setting that matches the product use context].` "Candid" and "natural" are the two words that get you the UGC look. |

Save the character reference to
`~/board/_active/ugc-ads-<YYYY-MM-DD>/01-character-ref.png`.

If you used Path 2 (Soul ID), include the Soul ID string in `character_lock`
and reference it in every chunk's prompt, Soul ID overrides per-chunk
appearance drift.

---

### Phase 3: Hook brainstorm (Chat 1)

Hand off to `prompts/01-hook-brainstorm.md` with this exact handoff:

> Help me generate five hook variations for a UGC ad for my app/product
> `[URL]`. Ask any clarifying questions you have before writing, tone, format,
> angles I've ruled out, the current ad I'm replacing.

The prompt file enforces:

- Ask first, write second (no proactive guessing on tone).
- 5 hooks, each ≤12 words, each from a different archetype (pain, curiosity,
  contrarian, proof, authority).
- Each hook must be sayable on camera in under 3s.
- Each hook must work as a standalone Chunk 1 voiceover line, no setup
  required.
- A "rejected" footer listing 3 hooks the model considered but cut, with one
  line each on why.

The user picks one. That line becomes `chunks[0].voiceover` in Phase 4.

Also load `../shared/hook-bank-100.md` as a reference bank, if none of the
generated 5 land, browse the 100-hook bank for an archetype that fits.

---

### Phase 4: Multi-chunk script (Chat 2)

Hand off to `prompts/02-multi-chunk-script.md` with the chosen hook + the
product brief.

The prompt produces a YAML matching `templates/multi-chunk-script.yaml`.
Schema is canonical, every field is mandatory unless flagged optional.

Default 5-chunk layout (mid-funnel punchy framework):

| # | Role | Runtime | Product visible? | Voiceover style |
|---|------|---------|------------------|-----------------|
| 1 | Hook | 4s | No | Chosen hook line from Chat 1 |
| 2 | Problem | 6s | No | Painful concrete moment the ICP recognises |
| 3 | Solution intro | 6s | Yes (`@product` tag) | "Then I tried [product name]" + first reveal |
| 4 | Proof / demo | 8s | Yes (`@product` tag, action shot) | Specific result, named mechanism, no hype words |
| 5 | CTA | 4s | Yes (held up to camera) | Clear single action + URL or offer |

For the **full-stack education framework** (Py47FzLdF9E, alternative path),
go 7 chunks: hook / problem / agitation / solution intro / mechanism /
proof / CTA. Use when the product needs explaining (B2B, new category).
Costs ~40% more credits but converts on cold audiences.

The skill emits the YAML AND a derived "per-chunk render block" for each
chunk via `templates/chunk-prompt-template.md`. Each render block has:

```
[universal_directions paste]
[chunk-specific: voiceover, runtime, product_tag, framing, include_product]
```

Save the YAML to
`~/board/_active/ugc-ads-<YYYY-MM-DD>/02-script.yaml` and the per-chunk render
blocks to
`~/board/_active/ugc-ads-<YYYY-MM-DD>/chunks/chunk-{N}-prompt.md`.

---

### Phase 5: Render each chunk (Seedance 2.0)

Hand off to `prompts/03-per-chunk-render.md` for the operational ritual.

For **each chunk** in order:

1. Open a new Higgsfield Seedance 2.0 tab (or use the MCP tool if connected
   via `higgsfield-connector`, see the `seedance-pipeline` skill for the
   Playwright/MCP path; this skill does not duplicate it).
2. Confirm character is loaded (avatar name OR Soul ID OR uploaded reference).
3. Confirm Element tag is loaded, for chunks where `include_product: true`,
   `@product` MUST be in the Elements panel. For `include_product: false`,
   REMOVE the tagged element before generating, otherwise the model
   hallucinates the product into the shot.
4. Paste the chunk-specific render block.
5. Aspect: **9:16** (vertical UGC).
6. Resolution: **720p** for iteration, **1080p** for final master only.
   (720p is 50% cheaper, see "Cost discipline" below.)
7. Duration: match `chunks[N].runtime` exactly. If the voiceover is too
   long, REDUCE the runtime first, never let Seedance speed up the
   delivery, it sounds rushed.
8. Generate. Plus plan ($49/mo) allows 4 chunks in parallel.
9. Download to
   `~/board/_active/ugc-ads-<YYYY-MM-DD>/chunks/chunk-{N}.mp4`.

Repeat until all chunks render cleanly. Budget **1.5× credits** for failed
renders, Seedance flags ~30% of UGC prompts first pass due to the content
filter (see `higgsfield-seedance` for the filter model).

**Voice consistency:** Once chunk 1 lands with a voice you like, use
Higgsfield's "Change Voice" button on every subsequent chunk and pick the
SAME voice. Voice consistency is the second biggest AI-look complaint after
character drift.

---

### Phase 6: Assembly in CapCut

Skill emits an assembly checklist matching `../shared/capcut-finishing.md`.
That shared recipe handles:

- Import chunks in order.
- Tighten cuts between chunks (no breathing gap > 0.3s).
- Speed adjustment: 80–90% on any chunk where the AI rushed delivery.
- B-roll overlay: cover hallucinated frames (e.g. head suddenly enlarges
  for 2s) with footage from an adjacent chunk + mute the audio for that
  sub-section.
- Auto-captions: enable, choose Classic preset, enable black outline,
  tighten and raise. (Captions are mandatory, 85% of UGC ads are watched
  with sound off in feed.)
- Music: optional soft bed (-18 LUFS under voice).
- Export: **1080p, 30fps, H.264, MP4**. The shared recipe has the exact
  QuickTime-safe settings.

Final export lands at
`~/board/_active/ugc-ads-<YYYY-MM-DD>/03-final-1080p.mp4`.

---

### Phase 7: Critique loop (Chat 3, optional but recommended)

Hand off to `prompts/04-critique-and-revise.md`, which dispatches to the
`higgsfield-ad-critic` sibling skill.

That skill:

1. Uploads `03-final-1080p.mp4` to Gemini for frame-by-frame analysis.
2. Returns a critique report: hook strength, product visibility timing,
   pacing, character drift, voice match, CTA clarity, AI-look tells.
3. Suggests per-chunk regenerations OR per-chunk CapCut fixes.

Apply the critique. If 1–2 chunks need regenerating, only redo those, do
NOT re-render the full ad. Loop until the critic green-lights.

Save the critique report to
`~/board/_active/ugc-ads-<YYYY-MM-DD>/04-critique-v{N}.md`.

---

### Phase 8: Ship-gate (MANDATORY, no exceptions)

Two ship-gates, both mandatory, both blocking:

1. **`content-engine` voice gate.** Run the final caption + on-screen text +
   CTA copy through `content-engine`. Hard-fails on em dashes, AI-writing
   clichés, support promises, outcome guarantees, "transform / unlock /
   game-changer / 10x / level up / crushing it / killing it / secret sauce /
   revolutionary." If it fails, rewrite, do not ship.
2. **`humanizer` slop gate.** Run the same text through `humanizer` to
   strip residual AI-writing patterns (negative parallelism, rule of three,
   inflated symbolism). If it rewrites anything material, apply the
   rewrite.

Only ship after both gates pass. Document the gate run in
`~/board/_active/ugc-ads-<YYYY-MM-DD>/05-ship-checklist.md`.

---

## File layout (output destination)

Every run writes to:

```
~/board/_active/ugc-ads-<YYYY-MM-DD>/
├── 00-product-still.png           ← Phase 1 product render
├── 01-character-ref.png           ← Phase 2 character reference
├── 02-script.yaml                 ← Phase 4 multi-chunk YAML (canonical)
├── 02-script-pasteable.md         ← Phase 4 derived: paste-ready aggregator
├── chunks/
│   ├── chunk-1-prompt.md          ← Phase 4 per-chunk render block
│   ├── chunk-1.mp4                ← Phase 5 rendered clip
│   ├── chunk-2-prompt.md
│   ├── chunk-2.mp4
│   ├── ... (one per chunk)
├── 03-final-1080p.mp4             ← Phase 6 CapCut export
├── 04-critique-v1.md              ← Phase 7 critique report (per loop iteration)
├── 04-critique-v2.md
├── 05-ship-checklist.md           ← Phase 8 gate results + final caption + hashtags
└── 06-brief.md                    ← Phase 0 captured intake (so future you can audit)
```

The dated folder is the contract, every other skill that consumes UGC ad
outputs (e.g. `apify-content-analytics` for post-flight scoring) reads from
this layout.

---

## Frameworks (mid-funnel punchy vs full-stack)

Two canonical frameworks lifted from Py47FzLdF9E. Pick at Phase 0.

### Mid-funnel punchy (default, 5 chunks, 25–35s)

For warm or problem-aware audiences. Lower credit cost, faster iteration.

```
1. Hook        4s  , pattern interrupt, no product
2. Problem     6s  , specific painful moment
3. Solution    6s  , product reveal + first-use
4. Proof       8s  , named mechanism + result
5. CTA         4s  , clear action + URL
```

Total: ~28s. ~5 chunks. ~5–8 credits per chunk on 720p Plus plan.

### Full-stack education (7 chunks, 45–60s)

For cold audiences, new product categories, B2B with unfamiliar mechanism.

```
1. Hook         4s  , pattern interrupt
2. Problem      6s  , specific painful moment
3. Agitation    6s  , what happens if unsolved (cost / time / risk)
4. Solution     6s  , product reveal
5. Mechanism    10s , WHY it works (the "secret", but not literally "secret")
6. Proof        10s , named result, named mechanism
7. CTA          4s  , clear action + URL
```

Total: ~46s. ~7 chunks. ~40% more credits than mid-funnel.

---

## Cost discipline (defaults baked in)

Lifted from Py47FzLdF9E + cross-cutting pattern #5 in the transcripts report.

| Lever | Default | Reason |
|-------|---------|--------|
| Resolution | **720p** for iteration, 1080p only for master | 50% cheaper. 720p in feed is indistinguishable from 1080p. |
| Plan | **Plus plan ($49/mo)** minimum | Below Plus you can't generate 4 chunks in parallel, wall clock for a 5-chunk ad goes from 12 min to 50 min. |
| Credit buffer | **1.5× planned credits** | ~30% of chunks fail filter or render badly. Plan for it. |
| Upscaling | **Never upscale**, regenerate instead | Upscaling adds artifacts. 1080p re-render is cleaner than 720p → 1080p upscale. |
| Voice | **Set once, reuse via Change Voice button** | Don't burn credits regenerating to fix a voice, use the per-clip Change Voice button. |
| Hallucination repair | **CapCut overlay, not regenerate** | A 2s head-enlargement bug gets covered by an adjacent chunk's B-roll, not by burning credits regenerating the whole 8s chunk. |

If a user is over budget on credits, the first move is ALWAYS:

1. Drop to 720p.
2. Cut from full-stack (7 chunks) to mid-funnel (5 chunks).
3. Reuse hooks across A/B tests instead of regenerating hook variants.

Never start by suggesting upscale or longer chunks.

---

## Multi-chunk schema reference

Canonical schema in `templates/multi-chunk-script.yaml`. Inline summary:

```yaml
campaign_name: string                      # human readable
character_lock:
  age: string                              # "early 40s" not "42"
  gender: string
  appearance: string                       # one paragraph, candid + natural
  voice: string                            # Higgsfield "Change Voice" name
  soul_id: string | null                   # if Soul ID path
  reference_image_path: string             # local path to character ref
universal_directions:
  hair: string                             # consistent style/colour across chunks
  application: string                      # how character interacts with product
  b_roll: string                           # consistent secondary footage rules
  ugc_realism_notes: string                # "selfie handheld, slight wobble, no perfect framing"
chunks:
  - id: 1
    role: hook | problem | agitation | solution | mechanism | proof | demo | cta
    voiceover: string                      # exact line, no on-the-nose
    runtime: integer                       # seconds (4, 6, 8, 10)
    product_tag: "@product" | null
    framing: string                        # "selfie handheld, eye-level, shoulders up"
    include_product: boolean               # if false, REMOVE Element tag before generating
final_cta:
  voiceover: string
  runtime: integer                         # default 4
  on_screen_url: string                    # optional overlay URL
```

The schema is loaded by Chat 2 and emitted as the canonical artefact.
Every per-chunk render block is derived from this.

---

## Shared assets (referenced, not duplicated)

These shared assets live at `../shared/` (parent: `higgsfield/skills/shared/`)
and are reused by every Higgsfield production skill. Read them inline, do
not re-author here:

| Asset | Path | Use |
|-------|------|-----|
| Prompt skeletons | `../shared/higgsfield-prompt-skeletons.md` | Skeleton 2 (video prompt) is the canonical per-chunk shape. |
| Element tagging | `../shared/element-tagging.md` | `@product` is mandatory for multi-chunk consistency. Read for upload + tag mechanics. |
| CapCut finishing | `../shared/capcut-finishing.md` | Post-production assembly recipe. Shared with `cinematic-ai-reels`, `motion-graphic-reels`. |
| Hook bank | `../shared/hook-bank-100.md` | 100 viral hook archetypes (scraped from Reddit, Py47FzLdF9E source). Chunk 1 fallback bank. |

If any of these shared files are missing, fall back to the inline patterns
documented in this SKILL.md, but flag the missing shared asset so it gets
authored.

---

## Skill dependencies (call these, do not re-implement)

Hard dependencies, this skill DOES NOT WORK without them:

| Skill | Where in the workflow | Why |
|-------|----------------------|-----|
| `seedance-pipeline` | Phase 5 (render step) | The actual Seedance 2.0 render via MCP or Playwright. This skill emits paste-ready prompts; `seedance-pipeline` runs them. |
| `higgsfield-soul` | Phase 2 (character lock, if Soul ID path) | Soul ID creation + per-chunk consistency. |
| `higgsfield-audio` | Phase 5 (per-chunk audio direction) | Lip-sync + dialogue audio rules per model. Seedance 2.0 generates dialogue inline, read this skill for the audio direction language that survives the filter. |
| `selrai-ad-image` | Phase 1 (product still, if no clean source) | Pre-mints the clean product image that feeds the `@product` Element tag. |
| `ad-creative` | Phase 4 (CTA copy variants) + Phase 0 (hook variations companion) | Generates copy variants for A/B testing the CTA card and the chosen hook. |
| `content-engine` | Phase 8 ship-gate (MANDATORY) | Voice filter. Hard-fails on em dashes, banned vocab, support promises, outcome guarantees. |
| `humanizer` | Phase 8 ship-gate (MANDATORY) | Slop blocklist. Wikipedia signs-of-AI-writing detector. |
| `higgsfield-ad-critic` | Phase 7 (critique loop, optional but recommended) | Sibling skill. Frame-by-frame Gemini analysis + per-chunk fix suggestions. |

Soft dependencies, use if available, fall back gracefully if not:

| Skill | Where | Fallback |
|-------|-------|----------|
| `higgsfield-recall` | Phase 0 + Phase 5 (auto, silent) | Reads prior failure DB, applies known fixes. If unavailable, run anyway, just lose the learned fixes. |
| `higgsfield-prompt` | Phase 4 (chunk prompt shape) | Canonical MCSLA prompt formula. If unavailable, use the inline skeleton in `templates/chunk-prompt-template.md`. |
| `higgsfield-seedance` | Phase 5 (preflight linter) | The 6-slot formula + filter diagnostic. If unavailable, run anyway, just lose the filter prediction. |
| `reels-hook-score` | Post-flight (after ad is live in feed) | Scores the ad on hook / hold / completion / saves / shares. Out of scope for the build, in scope for the next iteration. |

---

## Style constraints (Selr AI house style, non-negotiable)

These apply to EVERY text artefact this skill emits: voiceover lines, on-screen
text, captions, CTAs, brief docs.

Bans:

- No em dashes. Use commas or full stops.
- Banned vocab: "game-changer", "10x", "crushing it", "killing it", "secret
  sauce", "level up", "unlock", "transform", "transformative", "revolutionary",
  "ultimate", "next-level", "supercharge", "skyrocket", "elevate".
- No outcome guarantees ("you'll get N customers", "guaranteed results",
  "money-back").
- No drop-in invites ("come say hi", "DM me", "swing by").
- No personal-life mixing (no kids, no marriage, no health, no addiction
  narratives, Selr AI business context only).
- No support promises ("ongoing support", "weekly Q&A", "we're here for you").
- AU English (organise, optimise, colour, behaviour, realise).

Required:

- Specific over generic ("my Etsy store saved 4 hours/week", not "my business
  benefited").
- Named mechanism over magic ("the product uses [specific ingredient/feature]",
  not "this product just works").
- One CTA per ad. Multiple CTAs split attention.

The `content-engine` ship-gate enforces all of this. If anything slips
through, that's a bug in the gate, log it and fix.

---

## Anti-poaching boundary

This skill's triggers MUST NOT poach from:

- `ad-creative`, that skill is for **copy-only** variations (headlines,
  primary text, RSA, FB ad copy). If the user asks for "ad copy" without
  video, route there.
- `seedance-pipeline`, that skill is for **single-clip** Seedance generation.
  If the user asks for one 5–10s product video, route there. This skill only
  kicks in for multi-chunk (3+ clips with character lock).
- `selrai-ad-image`, that skill is for **single-image** ads (square IG ad for
  local business). Image-only.
- `motion-graphic-reels` / `cinematic-ai-reels`, those skills are for
  **non-product** reels (educational, B-roll-driven, no product as hero).
- `higgsfield-marketing-studio`, that sibling skill takes ONE brief and
  emits a full campaign (image + reel + carousel + copy). Higher level than
  this skill.
  multi-channel campaigns. Even higher level.

If a user asks for "a UGC ad", default to this skill. If the request says
"campaign" or "rollout" or "multi-channel", escalate to

---

## Failure modes + recovery

| Failure | Cause | Fix |
|---------|-------|-----|
| Seedance instant-fail (<10s) on a chunk | Content filter. Voice was wrong. | Apply `higgsfield-seedance` rewrite, describe the SCENE not the SUBJECT. 6-slot formula. |
| Seedance delayed-fail (>30s) | Render complexity. | Cut action density. Shorten runtime by 2s. Try again. |
| Character drift across chunks | No Soul ID + named avatar wasn't pinned. | Switch to Soul ID path (Phase 2 Path 2). Regenerate chunks 2+. |
| Product hallucinates in a no-product chunk | Element tag stayed loaded. | REMOVE `@product` from Elements panel before generating that chunk. |
| Voice changes between chunks | Different generated voice per chunk. | Use Change Voice button, pick one consistent voice across all chunks. |
| AI-look complaints | Too clean. No wobble. Perfect framing. | Add "selfie handheld, slight wobble, imperfect framing, candid" to `universal_directions.ugc_realism_notes`. |
| Hook lands flat | Hook was tested cold in Chat 1, not against current creative. | Pull from `../shared/hook-bank-100.md`. Different archetype. |
| Critique loop says product visibility too late | Product reveal in chunk 4 not chunk 3. | Pull the reveal forward. Chunk 3 ALWAYS introduces the product in mid-funnel framework. |
| Captions cut off voiceover lines | Auto-caption misread fast delivery. | CapCut: tighten cuts, move captions higher, re-export. |
| Final ad reads as "salesy" | CTA over-promises or uses banned vocab. | Run `content-engine` ship-gate. Re-write per its feedback. |

---

## Quick-start (for the impatient operator)

```
1. /skill higgsfield-ugc-ads
2. Answer Phase 0 questions (URL, runtime, character, voice, framework).
3. Skill writes 06-brief.md.
4. Skill invokes selrai-ad-image OR you upload a clean product photo.
5. Skill helps you pick character path (Higgsfield avatar / Soul ID / GPT Image).
6. Open Chat 1 → /skill prompts/01-hook-brainstorm.md → pick 1 of 5.
7. Open Chat 2 → /skill prompts/02-multi-chunk-script.md → review YAML.
8. For each chunk: paste chunk-{N}-prompt.md into Higgsfield Seedance 2.0.
9. Download chunks to chunks/chunk-{N}.mp4.
10. CapCut: assemble per ../shared/capcut-finishing.md.
11. Open Chat 3 → /skill prompts/04-critique-and-revise.md → apply suggestions.
12. content-engine + humanizer ship-gate on caption + on-screen text.
13. Ship.
```

A clean run end-to-end on Plus plan: 60–90 minutes, ~40–60 credits, $0 outside
the Plus subscription.

---

## Worked example

See `examples/sample-vitamin-bottle-ad.md` for a full worked example:
vitamin bottle product → 5-chunk mid-funnel punchy script → assembly → critique
loop → ship. Reproduces the Py47FzLdF9E flow with Selr-house-style voice.

---

## MCP / automation integration paths

Three operational paths for Phase 5 (the actual per-chunk render). Pick by
what's installed.

### Path A: Manual (lowest skill barrier, no MCP)

Operator opens Higgsfield Seedance 2.0 in the browser, pastes each chunk's
prompt, clicks Generate, downloads. No MCP, no scripting. This is the
default path documented in `prompts/03-per-chunk-render.md`.

**Best for:** First-time use of the skill. Single-ad runs. Operators who
want to see each chunk render and decide before continuing.

**Cost:** Same per-chunk credits. No tool-side overhead.

**Risk:** Operator skips a step (e.g. forgets to remove `@product` tag on a
no-product chunk). The pre-flight checklist in
`templates/chunk-prompt-template.md` covers this.

### Path B: MCP via higgsfield-connector

Higgsfield's official MCP server (`https://mcp.higgsfield.ai/mcp`) is
installed via `higgsfield-connector`. Claude calls the MCP tool directly
from Chat 2 to dispatch each chunk's render.

The pattern (per `/tmp/hewitt-skills-analysis.md` cross-skill patterns):
- Never hardcode the Higgsfield tool name (it's still evolving, was
  `text-to-video`, became `video-generation-v2`, etc.).
- Use `ToolSearch` with query `higgsfield` and pick the matching
  video-generation tool at runtime.
- Pass the chunk prompt + character reference + Element tag + runtime.
- Poll until complete. Download to
  `~/board/_active/ugc-ads-<YYYY-MM-DD>/chunks/chunk-{N}.mp4`.

**Best for:** Operators with `higgsfield-connector` installed. Batch runs.
Campaigns with 10+ chunks where manual is too slow.

**Cost:** Same per-chunk credits. ~5min wall-clock saved per chunk vs
manual (no browser tab-flipping).

**Risk:** MCP tool names drift. The `ToolSearch`-at-runtime pattern fixes
this.

### Path C: Playwright via seedance-pipeline

If MCP is not connected (or fails), `seedance-pipeline` drives Higgsfield
via Playwright. Each chunk is rendered by opening the Seedance 2.0 tab,
filling the prompt, clicking Generate, polling, downloading.

This skill emits the prompts; `seedance-pipeline` runs them. No code is
duplicated.

**Best for:** Operators with `seedance-pipeline` but no MCP. Repeatable
overnight batches.

**Cost:** Same per-chunk credits + Playwright tab time.

**Risk:** Higgsfield UI changes break the selectors. `seedance-pipeline`
maintains the selector library.

### Path decision matrix

| Path | MCP connected? | seedance-pipeline installed? | Recommended when |
|------|---------------|------------------------------|------------------|
| A, Manual | n/a | n/a | First-time use, single ad, want to inspect each chunk |
| B, MCP | YES | n/a | Repeat use, 5+ chunks, batch dispatch |
| C, Playwright | NO | YES | MCP unavailable but want automation |

Default in this skill: Path A unless `higgsfield-connector` is detected at
Phase 0 (in which case suggest Path B to the user).

---

## Comparison, when to use Marketing Studio instead of this skill

Higgsfield's **Marketing Studio** (documented in `higgsfield-apps`) is a
no-prompt path: paste product URL → pick format → click generate → one 10
or 15s clip. The `q0EavB5hml8` transcript walks through this.

Marketing Studio is great for what it does. It is NOT what this skill does.

| Question | Marketing Studio | This skill |
|----------|-----------------|------------|
| Length | 10 or 15s single clip | 25–60s multi-chunk |
| Character lock across clips | No (each format = different scene) | Yes (Soul ID + universal directions) |
| Product Element tagging | Auto (less control) | Manual `@product` tag (full control) |
| Voiceover script | Auto-derived from URL copy | Custom, voice-graded, framework-driven |
| Hook brainstorm | None | Chat 1, 5 archetypes |
| Critique loop | None | Chat 3, Gemini frame-by-frame |
| Ship-gate (voice + slop) | None | `content-engine` + `humanizer` mandatory |
| CapCut assembly | Stitch 4 outputs manually | Single coherent piece |
| Skill barrier | None, paste URL, click | Higher, multi-chunk YAML |
| Best for | Quick test, low-stakes, daily volume | Conversion-critical, brand-safe, campaign-grade |
| Cost | ~5–10 credits per generation | ~28 credits for a 5-chunk ad |

If a user asks "can I just paste my product URL and get an ad?", route to
Marketing Studio (`higgsfield-apps`) first. If they then say "but I want
control over the script / character / multiple chunks", come back here.

For the **multi-format stitch ad recipe** from `q0EavB5hml8` (Marketing
Studio + ChatGPT 5.5 + CapCut), see the `higgsfield-marketing-studio`
sibling skill (planned). That recipe sits between Marketing Studio (one
clip) and this skill (custom multi-chunk).

---

## Pre-flight quality checks (before any render in Phase 5)

A 6-item gate that catches the most expensive mistakes before they burn
credits. Run this at the start of Phase 5, before paste #1.

### Gate 1: Character reference exists and is correctly sized

```bash
ls -lh ~/board/_active/ugc-ads-<YYYY-MM-DD>/01-character-ref.png
```

- File exists.
- File size > 200KB (a thumbnail is too small for Higgsfield to lock to).
- Aspect 9:16 or close. Square works in a pinch.

### Gate 2: Product still exists and has `@product` tag in Higgsfield

```bash
ls -lh ~/board/_active/ugc-ads-<YYYY-MM-DD>/00-product-still.png
```

- File exists.
- In Higgsfield → Elements panel → `@product` (or your chosen tag) is
  visible in the autocomplete.
- Test the tag: type `@p` in any prompt input, `@product` should appear.

### Gate 3: YAML is valid and complete

```bash
# Confirm all required fields are filled (no empty strings):
grep -E '^\s*(voiceover|appearance|hair|application|b_roll|ugc_realism_notes):\s*""\s*$' \
  ~/board/_active/ugc-ads-<YYYY-MM-DD>/02-script.yaml
# Should return nothing. If anything returns, a required field is empty.
```

### Gate 4: Per-chunk render blocks exist for every chunk

```bash
for i in 1 2 3 4 5; do
  test -f ~/board/_active/ugc-ads-<YYYY-MM-DD>/chunks/chunk-${i}-prompt.md \
    && echo "chunk-${i}: OK" \
    || echo "chunk-${i}: MISSING"
done
```

All 5 (or 7 for full-stack) must be OK.

### Gate 5: Voice ban-list compliance on every voiceover

```bash
# Cheap grep, catches the most common violations:
grep -E -i 'game-changer|10x|crushing it|killing it|secret sauce|level up|unlock|transform|revolutionary|, ' \
  ~/board/_active/ugc-ads-<YYYY-MM-DD>/02-script.yaml
# Should return nothing. If anything returns, voiceover has banned vocab
# or em dashes. Fix in Chat 2 before rendering.
```

### Gate 6: Plan + credit balance check

- Confirm Plus plan ($49/mo) is active (or Pro plan if available).
- Confirm credit balance is ≥ (chunks × 5 × 1.5) for the buffer.
  - 5 chunks → ≥ 38 credits
  - 7 chunks → ≥ 53 credits
- If short, top up before starting, OR drop to 720p and accept the longer
  recovery on quality.

If any gate fails, do NOT start Phase 5. Fix the gap, re-run gates.

---

## Per-chunk failure recovery flowchart

When a chunk fails (filter rejection, render failure, or just looks wrong),
the cheapest fix is rarely "regenerate". Use this decision tree.

```
Chunk render returns "flagged" / "blocked" in <10s?
├── Yes → Content filter rejection (NOT a render failure).
│         1. Apply higgsfield-seedance 6-slot formula rewrite.
│         2. Remove specific trigger words: "cheap", "crap", "wrong" (these
│            often trigger comparative-advertising filter).
│         3. Tighten scene description (specific room, specific light source).
│         4. Re-paste. Should pass.
│         If still fails after 2 attempts: pull from a different angle
│         (problem → curiosity instead of problem → pain).
│
└── No → Render completed.
    ├── Output looks visually wrong?
    │   ├── Character drift → Re-attach reference image OR switch to Soul ID
    │   │                      path. Regenerate (cost: ~5 credits).
    │   ├── Product drift → Confirm @product tag is loaded. Regenerate.
    │   ├── Hallucinated frames → COVER IN CAPCUT (cost: $0).
    │   │   Overlay 0.5-1s of adjacent chunk's b-roll + mute audio.
    │   ├── Wrong background → Strengthen b_roll instruction in YAML.
    │   │                      Regenerate.
    │   └── Voice mismatch → Use Change Voice button (cost: $0).
    │
    └── Output looks fine but voiceover is rushed?
        ├── If clip plays naturally despite "rushed" → Ship it.
        │                                              The viewer reads it
        │                                              as conversational.
        └── If clip sounds genuinely rushed (>10% sped up):
            ├── Option A: CapCut speed to 80-90% (cost: $0).
            ├── Option B: Shorten voiceover line in YAML, regenerate
            │            (cost: ~5 credits).
            └── Pick whichever costs less. Usually A.
```

Print this flowchart at the start of Phase 5. Saves the most credits of any
single artifact in this skill.

---

## Operator runbook (one-page summary)

A condensed reference for the operator running this skill for the Nth time.
Skip everything above; this is the only page you need open during execution.

```
================================================================
              HIGGSFIELD UGC ADS, OPERATOR RUNBOOK
================================================================

PHASE 0, Confirm
  Capture: product URL, runtime, chunks, character, voice, framework, CTA.
  Write to 06-brief.md.

PHASE 1, Product still
  EITHER: upload clean photo → Elements → tag @product.
  OR: invoke selrai-ad-image → 00-product-still.png → Elements → @product.

PHASE 2, Character
  Pick: Higgsfield avatar (name) | Soul ID | uploaded reference.
  Save reference to 01-character-ref.png.

PHASE 3, Hook (Chat 1)
  Paste prompts/01-hook-brainstorm.md handoff.
  Pick 1 of 5 hooks. Run through content-engine. Lock.

PHASE 4, Script (Chat 2, fresh)
  Paste prompts/02-multi-chunk-script.md handoff with hook + YAML inputs.
  Receive 02-script.yaml + 5 chunk-{N}-prompt.md files.
  Style audit must self-pass before YAML emits.

PRE-FLIGHT
  Run 6 gates: reference / product / YAML / chunks / ban-list / credits.

PHASE 5, Render (per chunk, ~5 min × N)
  For each chunk:
    1. Toggle @product in Elements per include_product.
    2. Paste chunk-{N}-prompt.md into Seedance 2.0.
    3. 9:16, 720p, match runtime.
    4. Generate. Diagnose per flowchart.
    5. Apply Change Voice to match Chunk 1's voice.
    6. Download to chunks/chunk-{N}.mp4.

PHASE 6, CapCut assembly
  Import → tighten cuts → speed adjust → B-roll cover → captions → export.
  Save 03-final-1080p.mp4.

PHASE 7, Critique (Chat 3, fresh)
  Paste prompts/04-critique-and-revise.md with path to 03-final-1080p.mp4.
  Apply fixes (CapCut-first, single-chunk-regenerate-second).
  Loop until GREEN-LIGHT (cap 3 iterations).

PHASE 8, Ship gate
  Run caption + on-screen text through content-engine. Must PASS.
  Run same text through humanizer. Apply rewrites if any.
  Write 05-ship-checklist.md.
  Ship.

TOTAL TIME (5 chunks, clean run, Plus plan): 60-90 min
TOTAL CREDITS: ~28 (1.5× buffer: ~42)
================================================================
```

Tape this to the monitor.

---

## Maintenance + versioning

- Version bumps when: schema changes, new framework added, dependency skill
  contract changes, ship-gate rules change.
- Update `metadata.updated` and `metadata.version` together.
- Run `python3 ~/.claude/skills/higgsfield/validate.py` before any tag.
- Log changes in the parent `../../CHANGELOG.md` under this sub-skill.

### Future versions, known TODO

- v1.1: add `higgsfield-marketing-studio-stitch` as an alternative Phase 5
  path (single-chunk Marketing Studio outputs stitched in CapCut). See
  `q0EavB5hml8` transcript for the recipe.
- v1.2: add A/B variant generation, emit two YAMLs from one brief, one
  per hook archetype, render in parallel.
- v1.3: post-flight scoring via `reels-hook-score` once the ad is in feed.
  Loop the score back into Chat 2 to inform the next ad's hook archetype.
- v1.4: GHL CRM hand-off, write the chosen avatar + voice + framework
  combo to a GHL contact/tag pair so future runs can default to the
  best-performing combo.

---

## Why this skill exists (one paragraph)

Multi-chunk UGC ads are the highest-converting Higgsfield output for product
brands in 2026, but they break in a single chat because the character lock,
the product Element tag, and the per-chunk filter discipline together exceed
context budget. The Alex-Robinson pattern (Py47FzLdF9E) plus the Edmund-Yong
two-chat split (xyKxB8q7wQk) solve this by separating hook brainstorm,
production, and critique into three chats with one shared YAML artefact. This
skill encodes that workflow with Selr-house ship-gates, a Soul ID character
path for campaign reuse, and a CapCut assembly recipe shared with the
cinematic + motion-graphic reel skills, so the same operator can ship a
product UGC ad, an educational reel, and a brand carousel from one toolkit.
