# Prompt 02: Multi-chunk script (Chat 2)

**Chat purpose:** Build the full multi-chunk YAML for the UGC ad. Emits the
canonical artefact every per-chunk render block is derived from.

**Use in:** Chat 2 of the two-chat pattern. Inherits the chosen hook from
Chat 1. Inherits nothing else, Chat 2 is a fresh context.

---

## The handoff message (paste this verbatim)

> Build the multi-chunk UGC ad script for this product. Output a YAML matching
> `templates/multi-chunk-script.yaml`.
>
> **Product:** [product name], [one-line description]
> **Product URL:** [URL]
> **Product still:** [path to 00-product-still.png]
> **Character path:** [Higgsfield avatar name | Soul ID string | uploaded reference]
> **Character reference image:** [path to 01-character-ref.png]
> **Voice (Higgsfield Change Voice name):** [voice name]
> **Framework:** [mid-funnel punchy | full-stack education]
> **Chosen hook (from Chat 1, archetype + line):** [archetype], "[hook line]"
> **Total runtime target:** [25s / 30s / 45s / 60s]
> **Number of chunks:** [default 5 for mid-funnel, 7 for full-stack]
> **ICP:** [one-line ICP from Chat 1]
> **Product mechanism (what makes it work):** [specific named mechanism, e.g.
>   "5g of magnesium glycinate per capsule", "AI workflow that auto-tags every
>   contact in GHL", "custom-spec coffee bean roasted to 12-bar pressure"]
> **CTA action:** [what the viewer should do, visit URL, comment WORD, etc.]
>
> Write the YAML now. Then write a derived per-chunk render block for each
> chunk using the field skeleton from `templates/chunk-prompt-template.md`.
>
> Selr AI house style rules apply to every voiceover line:
>
> - No em dashes
> - Banned vocab: game-changer, 10x, crushing it, killing it, secret sauce,
>   level up, unlock, transform, transformative, revolutionary, ultimate,
>   next-level, supercharge, skyrocket, elevate
> - No outcome guarantees
> - No drop-in invites
> - AU English

---

## What the model must produce

### Artefact 1: The YAML (canonical)

```yaml
campaign_name: "[Product name], [framework], [date]"
character_lock:
  age: "[e.g. early 40s]"
  gender: "[e.g. woman]"
  appearance: "[one-paragraph: hair, build, expression style, wardrobe.
    Include the words 'candid' and 'natural' for UGC realism.]"
  voice: "[Higgsfield Change Voice name]"
  soul_id: "[ID string or null]"
  reference_image_path: "~/board/_active/ugc-ads-<date>/01-character-ref.png"
universal_directions:
  hair: "[consistent style across all chunks, e.g. 'shoulder-length brown,
    loosely tied back, slightly messy, no salon-perfect styling']"
  application: "[how the character interacts with the product, e.g. 'holds
    the bottle naturally in left hand, never centered to camera, occasionally
    glances at it']"
  b_roll: "[secondary footage rules, e.g. 'soft natural light through window
    behind character, kitchen counter visible, no studio look']"
  ugc_realism_notes: "[non-negotiable: selfie handheld framing, slight wobble,
    imperfect eye-level, occasional micro-pauses, no perfect speech cadence]"
chunks:
  - id: 1
    role: hook
    voiceover: "[chosen hook from Chat 1, verbatim, ≤12 words]"
    runtime: 4
    product_tag: null
    framing: "selfie handheld, eye-level, shoulders up, kitchen background"
    include_product: false
  - id: 2
    role: problem
    voiceover: "[specific painful moment the ICP recognises, 1–2 sentences,
      ≤18 words total]"
    runtime: 6
    product_tag: null
    framing: "selfie handheld, slightly lower angle, expression shifts to
      frustration"
    include_product: false
  - id: 3
    role: solution
    voiceover: "[product reveal, 'Then I tried [product name]...' or
      similar. ≤18 words. Names the product.]"
    runtime: 6
    product_tag: "@product"
    framing: "selfie handheld, character reaches off-screen and brings
      product into frame, holds at chest height"
    include_product: true
  - id: 4
    role: proof
    voiceover: "[specific result + named mechanism. ≤25 words. No hype words.]"
    runtime: 8
    product_tag: "@product"
    framing: "medium shot, character demonstrates product use (uncapping,
      applying, opening, match the product type)"
    include_product: true
  - id: 5
    role: cta
    voiceover: "[clear single action + URL or offer. ≤15 words.]"
    runtime: 4
    product_tag: "@product"
    framing: "selfie handheld, product held up to camera at chest height,
      direct eye contact with lens"
    include_product: true
final_cta:
  voiceover: "[same as chunks[4].voiceover if 5-chunk, or new line if
    full-stack 7-chunk]"
  runtime: 4
  on_screen_url: "[optional overlay URL]"
```

For the **full-stack 7-chunk framework**, insert two extra chunks between
chunks 3 and 4:

```yaml
  - id: 3.5  # renamed in actual output; this is the "agitation" chunk
    role: agitation
    voiceover: "[what happens if the problem stays unsolved, cost, time, risk.
      ≤22 words. Concrete not abstract.]"
    runtime: 6
    product_tag: null
    framing: "medium shot, character looks away thoughtfully, frustrated"
    include_product: false
  - id: 4.5  # the "mechanism" chunk
    role: mechanism
    voiceover: "[WHY the product works. Names the specific mechanism. ≤28
      words. Avoid the word 'secret' but reveal the secret.]"
    runtime: 10
    product_tag: "@product"
    framing: "medium close-up, product held at angle so camera reads the
      label/spec, character explains while pointing"
    include_product: true
```

Renumber all chunks sequentially in the actual YAML output.

### Artefact 2: Per-chunk render blocks (one file per chunk)

For each chunk in `chunks[]`, derive a render block matching
`templates/chunk-prompt-template.md`. Save each as
`~/board/_active/ugc-ads-<date>/chunks/chunk-{N}-prompt.md`.

The render block format:

```
=== UNIVERSAL DIRECTION (paste at top of every chunk prompt) ===

Character: [character_lock.appearance], age [character_lock.age], voice
[character_lock.voice]. Soul ID: [character_lock.soul_id or "none"].

Hair direction: [universal_directions.hair]
Product application style: [universal_directions.application]
B-roll context: [universal_directions.b_roll]
UGC realism: [universal_directions.ugc_realism_notes]

Aspect: 9:16 vertical. Resolution: 720p (iteration) or 1080p (final master).
Style: candid UGC, handheld, natural light, no studio look.

=== CHUNK {N} ({role}) ===

Voiceover: "[voiceover line, read by Higgsfield Change Voice [voice]]"
Runtime: {runtime}s (do NOT let Seedance speed up delivery to fit; reduce
runtime if voiceover doesn't fit naturally).
Product visible: [Yes / No]
Product Element tag: [@product / NONE, if NONE, REMOVE the tagged element
from the Elements panel before generating]
Framing: [framing]

Camera movement: [pick one from higgsfield-camera that fits: handheld follow,
slow push-in, static handheld, slight pan]
Lighting: [match universal b-roll lighting, natural window light, soft]
Mood: [match role, hook=intrigue, problem=frustration, solution=relief,
proof=confidence, cta=direct]

EXCLUDE: stock-photo perfection, studio lighting, multiple takes blended,
on-screen text, captions, watermarks, AI artifacts, em dashes in voiceover.
```

---

## Selr AI style check (inline, before emitting YAML)

Before emitting the YAML, the model MUST self-audit every voiceover line for:

- Em dashes → rewrite with commas or full stops
- Banned vocab → rewrite with concrete language
- Outcome guarantees → rewrite as observed result with specific time/quantity
- "Just" "really" "very" → cut filler
- Long words where short ones work → cut

If any line fails, fix it before emitting. Do not emit a YAML that needs a
follow-up rewrite, that wastes context.

---

## Aggregator output (paste-ready)

Also emit `~/board/_active/ugc-ads-<date>/02-script-pasteable.md` which is the
YAML + all per-chunk render blocks concatenated, separated by `---` dividers.
Used by the operator who wants to paste everything into Higgsfield in one
sitting without flipping between files.

This uses an aggregator pattern that collates per-chunk prompts into one sheet,
the Hewitt repo (see `/tmp/hewitt-skills-analysis.md`).

---

## Hand off to Phase 5

After Chat 2 finishes:

- `02-script.yaml` is the canonical artefact.
- `chunks/chunk-{N}-prompt.md` are the per-chunk render blocks.
- `02-script-pasteable.md` is the one-paste aggregator.

Move to Phase 5 (`prompts/03-per-chunk-render.md`). Chat 2 may stay open for
voiceover rewrites if Phase 5 reveals a line doesn't render well, but do
NOT open a new chunk's render context in Chat 2. Each chunk render lives in
the Higgsfield tab (or `seedance-pipeline` MCP call), not in Chat 2.

---

## Failure modes

| Failure | Cause | Fix |
|---------|-------|-----|
| Voiceover lines too long for runtime | Model padded with filler | Re-paste with explicit word counts per role (hook ≤12, problem ≤18, solution ≤18, proof ≤25, cta ≤15) |
| Chunk 3 doesn't reveal the product | Model deferred reveal to chunk 4 | Re-paste: "Mid-funnel framework REQUIRES product reveal in Chunk 3, not 4." |
| Banned vocab in proof chunk | Model defaulted to hype | Re-paste with banned vocab list inline + 2 example rewrites |
| Em dashes in any voiceover | Model trained on em-dash-heavy corpora | Re-paste with "REMINDER: NO EM DASHES ANYWHERE. Use commas or full stops." |
| Outcome guarantees in proof or CTA | Model defaulted to conversion language | Re-paste with: "Use observed-result language ('I now spend 4 hours less per week'), not guarantee language ('you'll save 4 hours per week')." |
| Per-chunk render blocks missing UGC realism notes | Model forgot to inherit universal directions | Re-paste: "Every chunk render block MUST start with the full universal_directions block, verbatim." |
