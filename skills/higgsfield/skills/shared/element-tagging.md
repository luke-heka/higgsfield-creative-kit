# Higgsfield Elements Tagging Convention (`@product` Consistency Primitive)

How to lock a product or recurring object into multi-chunk Higgsfield
generations so it appears identically across clips. Extracted from Alex
Robinson's UGC workflow.

Loaded by `higgsfield-ugc-ads`, `higgsfield-marketing-studio`,
`higgsfield-content-factory`, `higgsfield-viral-replicator`.

---

## What It Does

Higgsfield's Elements panel lets you upload an image asset (product,
character, logo, prop) and assign it a `@tag`. From then on, any prompt
that references `@tag` will composite that exact asset into the
generation.

This is the difference between:
- ❌ "She picks up a green bottle of vitamins" → AI invents a different
  green bottle every chunk
- ✅ "She picks up @bottle and twists off the cap" → exact same bottle
  every chunk

---

## When To Use

- Multi-chunk UGC ads where product visual must stay consistent
- Carousel image sets where the same product appears across slides
- Reels where a recurring character/brand asset must persist

If you only need ONE clip with the product, skip Elements — direct
description is fine.

---

## Setup (one-time per asset)

1. **Pre-render the asset clean.**
   - Use **Nano Banana 2** or **GPT Image 2.0** to generate the product
     on a pure white background.
   - Prompt example: *"Generate a high quality render of this image
     against a white background and remove the [distracting elements]."*
2. **Upload to Higgsfield → Elements panel.**
3. **Assign a short, memorable tag:** `@bottle`, `@shoe`, `@cup`,
   `@product`.
4. **Approve** so it persists across your account session.

Keep tag names lowercase, no spaces, no numbers if possible.

---

## Naming Convention (Selr AI house rules)

| Asset type | Tag pattern | Example |
|---|---|---|
| Hero product | `@product` (single asset) or specific noun | `@bottle`, `@cup`, `@board` |
| Recurring character | `@character` or named | `@megan`, `@founder` |
| Brand mark / logo | `@logo` | `@logo` |
| Recurring prop | `@prop` + noun | `@prop_laptop`, `@prop_phone` |
| Multiple products in same campaign | numbered | `@product_a`, `@product_b` |

Avoid tags that collide with Higgsfield's reserved system tokens
(`@avatar`, `@scene`, `@hook` — these are camera/preset tokens).

---

## Per-Chunk Usage

In each chunk's prompt, reference the tag explicitly:

```
Chunk 2: She walks into the kitchen holding @bottle. Close-up as she
twists off the cap and tips two capsules into her palm. Soft morning
light from the window.
```

The Higgsfield generator will composite the exact tagged asset.

---

## "No Tag" Chunks (Critical Pattern)

Not every chunk should include the product. Reels with too much product
on-screen feel like ads (lower watch time).

**Rule of thumb:** in a 5-chunk UGC ad:
- Chunks 1-2: NO product (hook, problem set-up). Remove tag from prompt.
- Chunks 3-4: Product present. Use `@product` tag.
- Chunk 5: CTA. Product hero shot, `@product` tag.

If your multi-chunk script flags a chunk as `include_product: false`,
**remove the tagged element from the Elements panel for that single
generation** (or omit the tag from the prompt — the generator won't
spontaneously add it).

---

## Tag Persistence Across Sessions

Tags persist in your Higgsfield account workspace, not per-project.

- **Pro:** generate today, return next week, same `@bottle` still works.
- **Con:** if you reuse the same tag for a new product, it overrides the
  old one across ALL projects using that tag.

**Workaround:** for new campaigns, mint fresh tags
(`@bottle_v2`, `@bottle_apr`). Disposable tag names are fine.

---

## Common Failure Modes

| Symptom | Cause | Fix |
|---|---|---|
| Tag ignored, product replaced with generic | Tag name too generic (e.g. `@thing`) | Re-tag with specific noun (`@vitamin_bottle`) |
| Product appears warped / partial in some chunks | Pre-render isn't clean (busy background) | Re-render the source asset with Nano Banana on white BG, re-upload |
| Two products in one chunk, both wrong | Using one tag for both | Use distinct tags (`@product_a`, `@product_b`) |
| Tag works in some chunks not others | Inconsistent prompt phrasing | Always introduce the tag with the same verb pattern ("holding @bottle", "picks up @bottle") |
| Character holding product disappears | Action too complex for one generation | Split into two chunks: introduction + interaction |

---

## Integration With Multi-Chunk Script Schema

The multi-chunk script object (used by `higgsfield-ugc-ads`) should
include a per-chunk `product_tag` field:

```yaml
chunks:
  - id: 1
    voiceover: "Have you ever had..."
    runtime: 4s
    product_tag: null      # no product visible in hook
    framing: medium close-up

  - id: 3
    voiceover: "I started using..."
    runtime: 6s
    product_tag: "@bottle" # product appears here
    framing: over-shoulder, hands holding bottle

  - id: 5
    voiceover: "Get yours at..."
    runtime: 4s
    product_tag: "@bottle" # hero shot
    framing: close-up, product centred
```

The skill emits prompts with the tag injected only where `product_tag`
is set.
