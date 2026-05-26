# DTC E-commerce, 3 Paste-Ready Seedance 2.0 Chunk Prompts

Three Skeleton-2 (video) prompts, one per stage of the 5-chunk script. Each is paste-ready into Higgsfield Seedance 2.0 after you swap the `{{VARIABLES}}` for your brand's values.

Render settings for all three: **9:16, 720p, handheld selfie, Higgsfield "Change Voice" set to the same voice across all chunks.**

This file ships the **HOOK** (chunk 1), the **SOLUTION** (chunk 3), and the **CTA** (chunk 5). Chunks 2 and 4 follow the same template, adapted with the role-specific framing from `chunk-prompt-template.md`.

---

## CHUNK 1, HOOK (4 seconds, no product visible)

**Before pasting:** confirm the `{{PRODUCT_TAG}}` Element is REMOVED from the Higgsfield Elements panel. The hook must be product-free.

```
4 seconds 9:16, medium close-up handheld selfie style, woman in her late
20s looking directly at the lens with a slight tired wide-eyed expression
then snapping back to camera on the hook word, modern apartment bathroom
soft morning light from a window at camera-right no fill no key, golden
hour 7am natural soft lighting, static handheld with slight natural wobble
no zoom no pan, 50mm equivalent shallow depth of field background gently
out of focus, warm muted palette cream and soft brown, fine film grain
natural skin texture not plastic, audio: natural ambient bathroom room
tone her voiceover playing over: "{{BEFORE_PAIN}} until I started doing
this every morning", product not visible in frame, EXCLUDE: AI-glossy
skin, plastic shine, hyper-saturated colors, gradient backgrounds, drop
shadows, emoji, watermark, overlay text, stock-photography poses, fake
smiles, perfect spokesperson delivery, infomercial energy, studio
lighting, 4K cinema look, dolly shots, crane shots, tripod stability
```

---

## CHUNK 3, SOLUTION (6 seconds, product enters frame)

**Before pasting:** confirm the `{{PRODUCT_TAG}}` Element IS loaded in the Higgsfield Elements panel. Test by typing `@`, your product tag should autocomplete.

```
6 seconds 9:16, medium close-up handheld selfie style, woman in her late
20s reaching off-screen and bringing {{PRODUCT_TAG}} into frame at chest
height with a small natural smile starting at the corners of her mouth as
she does it, modern apartment bathroom soft morning light from a window
at camera-right, golden hour 7am natural soft lighting, slight handheld
pan as the product enters frame no zoom, 50mm equivalent shallow depth of
field background gently out of focus, warm muted palette cream and soft
brown, fine film grain natural skin texture, audio: natural ambient
bathroom room tone her voiceover playing over: "Then I picked up
{{PRODUCT_NAME}} and used it the way it actually says on the box",
product {{PRODUCT_TAG}} clearly visible held in hand at chest height for
the last 3 seconds label facing camera at a slight angle not squared,
EXCLUDE: AI-glossy skin, plastic shine, hyper-saturated colors, gradient
backgrounds, drop shadows, emoji, watermark, overlay text, stock-photography
poses, fake smiles, perfect spokesperson delivery, infomercial energy,
fake enthusiasm, product hero shot with rim light, before-after split
screen, dolly shots, crane shots, tripod stability
```

---

## CHUNK 5, CTA (4 seconds, product held up)

**Before pasting:** `{{PRODUCT_TAG}}` Element still loaded in the Higgsfield Elements panel from chunk 3 and 4.

```
4 seconds 9:16, medium close-up handheld selfie style, woman in her late
20s holding {{PRODUCT_TAG}} up at chest height beside her face with a
soft smile and direct eye contact with the lens, modern apartment bathroom
soft morning light from a window at camera-right, golden hour 7am natural
soft lighting, static handheld with slight natural wobble no zoom no pan,
50mm equivalent shallow depth of field background gently out of focus,
warm muted palette cream and soft brown, fine film grain natural skin
texture, audio: natural ambient bathroom room tone her voiceover playing
over: "It's {{OFFER}} at {{SHIPPING_URL}}, linked in bio", product
{{PRODUCT_TAG}} clearly visible held at chest height beside her face for
the full 4 seconds label facing camera at a slight angle, EXCLUDE:
AI-glossy skin, plastic shine, hyper-saturated colors, gradient
backgrounds, drop shadows, emoji, watermark, overlay text, stock-photography
poses, fake smiles, perfect spokesperson delivery, infomercial energy,
product hero shot with rim light, "shop now" closing card, logo bug
overlay, dolly shots, crane shots, tripod stability
```

---

## Notes for the operator

- **Voice consistency:** after chunk 1 renders with a voice you like, hit the **Change Voice** button on chunks 2, 3, 4, 5 and pick the SAME voice. Do not let Seedance auto-pick per chunk.
- **Element tag toggle:** the single most-skipped step. Chunks 1 and 2 = tag REMOVED. Chunks 3, 4, 5 = tag LOADED. Skipping this is ~60% of "the product looks wrong" complaints.
- **Voiceover word counts:** all three prompts above are within the role-cap (hook ≤12 words, solution ≤18 words, CTA ≤15 words). If you swap copy, re-count.
- **No banned vocab:** these prompts deliberately avoid "game-changer", "unlock", "transform", "10x". If you swap copy, do not introduce them, the `content-engine` ship-gate hard-fails on them.
- **Filter discipline:** chunk 2 ("problem") and chunk 4 ("proof") have a slightly higher Seedance filter rejection rate because they describe past failure. If they instant-fail in under 10 seconds, the fix is in `higgsfield-seedance` 6-slot rewrite, describe the SCENE not the SUBJECT (e.g. "bathroom counter with three open bottles" not "I'd wasted hundreds on bad serums").
