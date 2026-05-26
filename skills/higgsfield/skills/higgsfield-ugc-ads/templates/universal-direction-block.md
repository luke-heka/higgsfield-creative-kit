# Universal Direction Block

**Purpose:** The "shared header" pasted at the top of every chunk's render
block. Lifted directly from the Alex-Robinson multi-chunk pattern
(Py47FzLdF9E). Enforces character + product + style consistency across all
chunks.

**Use:** Filled in once at Chat 2 from `character_lock` + `universal_directions`
in `templates/multi-chunk-script.yaml`. Then pasted verbatim at the top of
every `chunks/chunk-{N}-prompt.md`.

---

## Template (fill from YAML, then paste at top of every chunk prompt)

```
=== UNIVERSAL DIRECTION (paste at top of every chunk prompt) ===

CHARACTER
- Subject: [character_lock.appearance]
- Age: [character_lock.age]
- Gender: [character_lock.gender]
- Voice (apply via Higgsfield Change Voice button): [character_lock.voice]
- Soul ID (if applicable): [character_lock.soul_id or "none, using reference image"]
- Reference image: [character_lock.reference_image_path]

HAIR
[universal_directions.hair]
(Keep identical across every chunk. Any hair change between chunks reads as
a different person, the single biggest character-drift tell.)

PRODUCT APPLICATION
[universal_directions.application]
(Same hand, same hold style, same eye direction across chunks.)

B-ROLL CONTEXT
[universal_directions.b_roll]
(Same room, same light source, same surface tones across chunks.)

UGC REALISM (non-negotiable)
[universal_directions.ugc_realism_notes]
Plus these defaults that apply to EVERY UGC ad chunk:
- Selfie handheld framing
- Slight wobble (no gimbal-perfect motion)
- Imperfect eye-level (sometimes slightly low or high)
- Occasional micro-pauses in delivery (the character isn't reading a script)
- No studio look
- No salon-perfect hair
- No magazine-perfect skin
- Natural light only, no rim light, no key light, no fill light

TECHNICAL
- Aspect: 9:16 vertical
- Resolution: 720p (iteration) / 1080p (final master only)
- Style descriptor: "candid UGC, handheld, natural light, no studio look"

UNIVERSAL EXCLUDE LIST
- stock-photo perfection
- studio lighting
- multiple takes blended into one shot
- on-screen text (captions added later in CapCut)
- watermarks
- AI rendering artifacts (extra fingers, melting edges, morphing background)
- em dashes in voiceover text
- banned vocab in voiceover: game-changer, 10x, crushing it, killing it,
  secret sauce, level up, unlock, transform, revolutionary, ultimate,
  supercharge, skyrocket, elevate
- outcome guarantees in voiceover
- support promises ("we're here for you", "ongoing support")
```

---

## Why every chunk gets the universal block (not just chunks 2+)

You might think Chunk 1 doesn't need the universal block because it's the
hook and there's no comparison chunk yet. Wrong. Chunk 1 sets the visual
reference all subsequent chunks try to match. If Chunk 1 doesn't lock the
character + hair + framing + lighting, Chunks 2–5 will drift toward
whatever the model thinks "looks right" for each role.

Always paste the full universal block at the top of every chunk. The
incremental token cost is negligible. The consistency win is the whole point
of the multi-chunk pattern.

---

## Customisation per product type

The universal block is product-type-agnostic, but a few additions help:

| Product type | Universal-directions additions |
|--------------|-------------------------------|
| Supplements / capsules | `application`: "uncaps bottle with thumb, taps one capsule into palm, never shows pills falling" |
| Skincare / lotion | `application`: "pumps lotion onto back of hand, doesn't smear onto camera" |
| Apparel | `application`: "holds garment by collar, never wears it (avoids body-morph artifacts)" |
| App / SaaS | `b_roll`: "laptop or phone screen visible in 1/4 of frame, screen content stays static" |
| Food / drink | `application`: "no chewing on camera (lip-sync artifacts), taste reaction only after frame cut" |
| Device / gadget | `application`: "demonstrates one feature per chunk, never multi-feature in one chunk" |

Add these to `universal_directions.application` in the YAML before emitting
chunk prompts.

---

## Common mistakes (avoid these)

| Mistake | Consequence | Fix |
|---------|-------------|-----|
| Different hair description per chunk | Character reads as a different person | Lock `universal_directions.hair` once, paste verbatim. |
| Universal block only on chunks 2+ | Chunk 1 sets a different reference, all subsequent chunks drift | Paste universal block on Chunk 1 too. |
| Generic "natural light" | Model interprets it differently per chunk (window light, sun, overcast) | Specify: "soft natural light through a window at camera-right". |
| Application instruction is vague | Hand position drifts per chunk | Name the hand, the hold, the angle, the eye direction. |
| Excluding "captions" but voiceover has captions in another language | Model thinks captions ≠ subtitles and adds subtitles | Exclude both: "on-screen text, captions, subtitles, lower thirds". |

---

## Worked example (fully filled)

```
=== UNIVERSAL DIRECTION (paste at top of every chunk prompt) ===

CHARACTER
- Subject: a candid, natural woman in her early 40s, lightly tanned, soft
  features, no makeup, wearing a heather grey cotton t-shirt
- Age: early 40s
- Gender: woman
- Voice (apply via Higgsfield Change Voice button): Megan
- Soul ID (if applicable): none, using reference image
- Reference image: ~/board/_active/ugc-ads-2026-05-24/01-character-ref.png

HAIR
Shoulder-length brown, loosely tied back, slightly messy, no salon styling,
flyaways visible. Identical in every chunk.

PRODUCT APPLICATION
Holds the bottle in her left hand at chest height. Never centered to camera.
Occasionally glances at the label but mostly looks at the lens. Uncaps with
right hand thumb, taps one capsule into right palm, does not show capsule
contents.

B-ROLL CONTEXT
Modern apartment kitchen. Soft natural light through a tall window at
camera-right. Wood countertop, ceramic mug to the left, succulent plant
visible just out of focus behind her. Same setup across every chunk.

UGC REALISM (non-negotiable)
Selfie handheld, slight wobble, imperfect framing (sometimes slightly low
or high), candid, no studio look, micro-pauses in delivery, occasional
glance away from lens before returning. Skin texture visible, no smoothing.

TECHNICAL
- Aspect: 9:16 vertical
- Resolution: 720p (iteration)
- Style descriptor: candid UGC, handheld, natural light, no studio look

UNIVERSAL EXCLUDE LIST
- stock-photo perfection, studio lighting, multiple takes blended, on-screen
  text, captions, subtitles, lower thirds, watermarks, AI rendering
  artifacts (extra fingers, melting edges, morphing background, eye drift),
  em dashes in voiceover, banned vocab (game-changer, 10x, crushing it,
  killing it, secret sauce, level up, unlock, transform, revolutionary),
  outcome guarantees, support promises
```

That block goes at the top of `chunk-1-prompt.md` through
`chunk-5-prompt.md`, verbatim. The per-chunk specifics (voiceover, runtime,
product_tag, framing, include_product) get appended underneath via
`templates/chunk-prompt-template.md`.
