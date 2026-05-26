# Real Estate Agent, Supporting Image Prompts

Three ready-to-render Higgsfield image prompts (Skeleton 1 format) for
slide 4 or slide 7 supporting imagery in real estate carousels. The
carousel slides themselves are rendered by `carousel-generator`, these
prompts only produce the background photo referenced from inside a slide.

Aspect ratio is 4:5 vertical to match Instagram carousel native
dimensions.

Replace `{{...}}` placeholders before rendering. Run each through the
Higgsfield MCP `generate_image` tool (GPT Image 2.0 for the
person-in-frame shot, Nano Banana 2 for the suburb map, Flux for the
exterior hero).

CASA-safe by default: no drone-over-private-property framing.

---

## 1. THE MOST PASTE-READY ONE, kerbside agent shot (slide 4)

Use this for any real estate carousel that needs an "agent on location"
or "this is who I am locally" supporting shot. Works for case-study and
tips templates.

```
4:5 vertical 2K resolution, medium shot from waist-up slight low angle,
a {{age_range}} real estate agent in an open-collar branded polo or
shirt (no full suit) standing kerbside in front of a {{typical_property_type}}
in {{suburb}} {{state}} with one hand resting casually in pocket looking
at the camera with a calm professional smile, mid-morning natural daylight
slightly overcast soft and even, suburban Australian streetscape with
mature trees and a brick or rendered home partly visible behind, 50mm
equivalent moderate depth of field background partly soft house clearly
identifiable as architectural style, neutral palette warm beige
brickwork green foliage and one branded accent colour on the polo,
photographic grain natural fabric and skin texture not retouched, no
visible street number on the house, no number plates on parked cars,
EXCLUDE: full suit and tie, sales-pose hand-on-hip, drone angle,
aerial view, AI-glossy skin, plastic shine, hyper-saturated colors,
gradient backgrounds, drop shadows, emoji, watermark, overlay text,
stock-photography pose, agency-headshot studio lighting, fake smile,
agency aesthetic, identifiable house number, identifiable number plate
```

---

## 2. Suburb-fact map overlay (cheat-sheet slide 7)

For the `carousel-cheat-sheet` template. Slide 7 shows the suburb as a
context anchor for the median / DOM / growth-rate data overlaid in the
slide. Top-down map style, licensed cartography aesthetic, not aerial
photography (CASA-safe).

```
4:5 vertical 2K resolution, top-down map illustration style, a clean
stylised cartographic view of {{suburb}} {{state}} with main roads
marked in soft grey lines parks shown as muted green polygons and
residential blocks shown as soft cream, no satellite imagery no aerial
photograph, light flat-design vector aesthetic with subtle paper texture,
neutral palette cream background soft sage green parks warm grey roads
and one {{brand_accent_color}} accent marking a small pin or highlighted
zone, no street names rendered (added later as overlay text), no real
property addresses visible, soft photographic grain over the flat
illustration to avoid plastic vector look, plenty of negative space in
the upper third of frame for data overlay text added later, EXCLUDE:
satellite imagery, drone photography, Google Maps screenshot aesthetic,
3D buildings, hyper-saturated colors, gradient backgrounds, drop
shadows, emoji, watermark, overlay text already rendered, agency
aesthetic, identifiable street names, identifiable house numbers
```

---

## 3. Property exterior hero (case-study slide 4)

For the `carousel-case-study` template. Slide 4 shows the property
exterior of a recent sale. Ground-level photography aesthetic, not a
drone shot, with permission-safe framing (no identifiable street number,
no number plates).

```
4:5 vertical 2K resolution, three-quarter front-on ground-level shot, a
{{typical_property_type}} ({{bed_bath_car}} configuration) in {{suburb}}
photographed from the kerb at slight angle showing the front facade
driveway and entry, mature trees and landscaped front garden partly in
frame, late afternoon golden hour light warm and directional shadows
soft and long, 35mm equivalent moderate depth of field property in sharp
focus background trees soft, palette matched to property style (warm
brick + cream render, or coastal weatherboard + matte black, or modern
charcoal + timber), photographic grain natural texture brick render
glass and timber, no people in frame, no visible street number, no
number plates on parked cars on the street, EXCLUDE: drone angle,
aerial view, fish-eye distortion, real estate brochure HDR look,
hyper-saturated sky, gradient backgrounds, drop shadows, emoji,
watermark, overlay text, stock-photography pose, agency aesthetic,
identifiable street number, identifiable number plate, sold sticker
overlay
```

---

## Notes

- Run prompt 1 first. It's the lowest-risk, highest-reuse shot for real
  estate carousels. Save it once and reference from multiple slides.
- Prompt 2 is for the suburb cheat-sheet template (20% of the rotation).
  The flat illustration aesthetic avoids satellite-imagery licensing and
  CASA drone rules.
- Prompt 3 is for case-study slots (30% of the rotation). Always pair
  with a real recent sale and written permission to reference.
- Save renders to `~/board/_active/content-factory-<DATE>/03-generate/
  batch-NN/<carousel-slug>/supporting-images/`.
- Cost: ~5 Higgsfield credits per image on GPT Image 2.0, ~3 on Nano
  Banana 2, ~7 on Flux.

---

## See also

- `~/.claude/skills/higgsfield/skills/shared/higgsfield-prompt-skeletons.md`
  Skeleton 1 full reference.
- `../shared/element-tagging.md`, `@agent` tag if the same agent needs
  to appear consistently across multiple supporting shots.
