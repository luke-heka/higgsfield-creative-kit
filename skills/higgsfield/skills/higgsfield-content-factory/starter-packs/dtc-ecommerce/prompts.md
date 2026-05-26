# DTC Ecommerce, Supporting Image Prompts

Three ready-to-render Higgsfield image prompts (Skeleton 1 format) for
slide 4 or slide 7 supporting imagery in DTC carousels. The carousel
slides themselves are rendered by `carousel-generator`, these prompts only
produce the background photo/product shot referenced from inside a slide.

Aspect ratio is 4:5 vertical to match Instagram carousel native dimensions.

Replace `{{...}}` placeholders before rendering. Run each through the
Higgsfield MCP `generate_image` tool (GPT Image 2.0 or Nano Banana 2
recommended).

---

## 1. THE MOST PASTE-READY ONE, kitchen counter product demo (slide 4)

Use this for ANY DTC carousel that needs a "here's the product in real
life" supporting shot. Lands on GPT Image 2.0 first try, no character
consistency needed.

```
4:5 vertical 2K resolution, overhead 45-degree angle shot, a {{product_name}}
bottle/jar/tube sitting on a clean light wood kitchen counter next to a
half-full glass of water and a folded linen napkin, modern home kitchen
with white subway tile splashback partly out of frame in background,
mid-morning natural light streaming from a window to the left soft and
warm, 35mm equivalent shallow depth of field background gently soft,
warm muted palette cream and soft beige with one subtle {{brand_accent_color}}
accent on the product label, fine photographic grain natural cotton and
ceramic textures not plastic, product {{product_name}} centered slightly
left clearly readable label facing camera, EXCLUDE: studio lighting,
seamless white backdrop, hyper-saturated colors, AI-glossy shine on the
product, plastic-looking textures, stock photography pose, gradient
background, drop shadows, emoji, watermark, overlay text, hashtag overlays,
fake smile model, agency aesthetic
```

---

## 2. Mirror selfie before-state (case-study slide 4)

For the case-study carousel template, slide 4 shows the customer's
"before" state. NOT the product. Sets up the transformation reveal on
slide 5.

```
4:5 vertical 2K resolution, mirror selfie medium shot, a {{age_range}}
{{gender}} customer-profile person in casual at-home clothes (oversized
t-shirt, hair tied back, no makeup) holding a phone to take a mirror
selfie in their bathroom, neutral expression slight tiredness around the
eyes that reads as honest not sad, modern home bathroom with white tile
and a wooden vanity, soft overhead bathroom lighting natural not
fluorescent, 28mm phone-camera equivalent, muted desaturated palette
cool greys and soft cream, photographic grain natural skin texture pores
visible not retouched, product not visible in this frame, on-screen
disclosure text "Customer profile, not a specific person" small bottom
corner if AI-generated, EXCLUDE: AI-glossy skin, plastic shine,
hyper-saturated colors, gradient backgrounds, drop shadows, emoji,
watermark, hashtag overlays, stock-photography poses, fake smiles,
heavy makeup, agency aesthetic, ring-light eye reflections
```

---

## 3. Ingredient hero shot (cheat-sheet slide 7)

For the ingredient-glossary cheat-sheet template, slide 7 shows the
ingredient itself, isolated. Educational, not product-promotional.

```
4:5 vertical 2K resolution, extreme close-up macro shot, a small pile of
raw {{ingredient_or_mechanism}} (powder, leaves, seeds, or extract drops)
arranged on a clean matte ceramic dish, surface only partly visible
ceramic edge soft on the right side of frame, soft diffused window
light from above creating gentle shadow definition, 100mm macro lens
extremely shallow depth of field only the ingredient in sharp focus
background and dish edges soft, natural earth palette warm browns
greens or creams matched to the actual ingredient color, photographic
grain natural texture grains and surfaces visible, no product packaging
in frame ingredient only, EXCLUDE: studio strobe lighting, glossy
artificial reflections, hyper-saturated colors, gradient backgrounds,
drop shadows, emoji, watermark, overlay text, stock-photography
arrangement, fake sparkles, agency aesthetic, plastic-looking textures
```

---

## Notes

- Run prompt 1 first. It's the lowest-risk, highest-reuse shot. If
  Higgsfield is offline, paste this into the Higgsfield web UI manually.
- Prompts 2 and 3 are situational. Skip them if the carousel doesn't
  need that slide type.
- Save renders to `~/board/_active/content-factory-<DATE>/03-generate/
  batch-NN/<carousel-slug>/supporting-images/`.
- Cost: ~5 Higgsfield credits per image on GPT Image 2.0, ~3 on Nano
  Banana 2.

---

## See also

- `~/.claude/skills/higgsfield/skills/shared/higgsfield-prompt-skeletons.md`
  Skeleton 1 full reference.
- `../shared/element-tagging.md`, `@product` tag if the same bottle
  needs to appear across multiple supporting shots.
