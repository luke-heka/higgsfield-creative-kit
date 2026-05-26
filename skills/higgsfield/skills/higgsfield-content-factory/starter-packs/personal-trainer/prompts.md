# Personal Trainer, Supporting Image Prompts

Three ready-to-render Higgsfield image prompts (Skeleton 1 format) for
slide 4 or slide 7 supporting imagery in PT carousels. The carousel
slides themselves are rendered by `carousel-generator`, these prompts
only produce the background photo referenced from inside a slide.

Aspect ratio is 4:5 vertical to match Instagram carousel native
dimensions.

Replace `{{...}}` placeholders before rendering. Run each through the
Higgsfield MCP `generate_image` tool (GPT Image 2.0 recommended for the
person-in-frame shots, Nano Banana 2 for the equipment macro).

---

## 1. THE MOST PASTE-READY ONE, gym-floor coaching shot (slide 4)

Use this for any PT carousel that needs a "this is where I coach" or
"this is what the session looks like" supporting shot. Female-coachable
framing by default (no shirtless flexing, no intimidating angles).

```
4:5 vertical 2K resolution, medium shot from chest-up slightly low angle,
a {{age_range}} personal trainer in a fitted branded t-shirt and shorts
standing on the gym floor next to a squat rack with one hand resting on
the barbell looking at the camera with a calm focused expression, modern
{{gym_setting}} commercial gym interior with rubber flooring and matte
black equipment, mid-morning natural light from a roller-door window to
the left soft and slightly cool, 50mm equivalent shallow depth of field
background gym soft and out of focus, neutral muted palette charcoal grey
matte black and warm beige skin tones, photographic grain natural fabric
and skin texture not retouched, no logos or product visible, EXCLUDE:
studio strobe lighting, fluorescent gym ceiling glare, shirtless flex,
six-pack hero shot, intimidating angle, AI-glossy skin, plastic shine,
hyper-saturated colors, gradient backgrounds, drop shadows, emoji,
watermark, overlay text, stock-photography pose, ring-light eye
reflection, agency aesthetic
```

---

## 2. Form-fix split-screen reference (mistakes / form-cue slide 4)

For the `carousel-mistakes` template. Slide 4 references a "wrong way /
right way" comparison. This prompt produces ONE side of the split
(usually the "right way" reference image, the "wrong way" stays as text
overlay or is shot live).

```
4:5 vertical 2K resolution, side-on full-body shot, a {{age_range}}
{{gender_of_client}} client in plain training clothes performing the
bottom of a {{exercise_name}} with correct form (e.g. neutral spine,
heels flat, knees tracking over toes), modern commercial gym interior
with soft natural light from one side, 35mm equivalent moderate depth of
field background partly soft, neutral palette warm grey rubber floor
matte black equipment and natural skin tones, photographic grain natural
fabric and skin texture, on-screen annotation space left clear in the
top third of the frame for arrow or circle overlay added later,
EXCLUDE: front-on hero pose, gym selfie angle, fluorescent ceiling
glare, AI-glossy skin, plastic shine, hyper-saturated colors, gradient
backgrounds, drop shadows, emoji, watermark, stock-photography pose,
fake smile, agency aesthetic
```

---

## 3. Equipment / programme card hero (cheat-sheet slide 7)

For the `carousel-cheat-sheet` template. Slide 7 shows the programme
artifact itself, a notebook, an RPE chart, a kettlebell on a mat,
isolated and educational.

```
4:5 vertical 2K resolution, overhead 45-degree angle shot, a
{{equipment_or_artifact}} (e.g. a hardcover training notebook open to a
handwritten programme page, or a single kettlebell on a rubber mat next
to a coffee cup) on a clean concrete or dark rubber gym floor, modern
gym corner partly visible at frame edge, soft diffused light from a
window or skylight no harsh shadows, 35mm equivalent shallow depth of
field artifact in sharp focus background soft, neutral palette charcoal
grey matte black and one warm accent (notebook paper cream or coffee
crema), photographic grain natural texture rubber paper leather and
metal visible, no people in frame, no branded logos visible, EXCLUDE:
studio strobe lighting, glossy artificial reflections, hyper-saturated
colors, gradient backgrounds, drop shadows, emoji, watermark, overlay
text, stock-photography arrangement, agency aesthetic, plastic-looking
textures
```

---

## Notes

- Run prompt 1 first. It's the lowest-risk, highest-reuse shot for
  PT carousels. Save it once and reference it from multiple slides.
- Prompt 2 is paired with the `carousel-mistakes` template, the most
  frequent template in the PT rotation (30%). Skip if a carousel
  doesn't need a form reference.
- Prompt 3 is occasional, only when the cheat-sheet template needs a
  hero artifact.
- Save renders to `~/board/_active/content-factory-<DATE>/03-generate/
  batch-NN/<carousel-slug>/supporting-images/`.
- Cost: ~5 Higgsfield credits per image on GPT Image 2.0, ~3 on Nano
  Banana 2.

---

## See also

- `~/.claude/skills/higgsfield/skills/shared/higgsfield-prompt-skeletons.md`
  Skeleton 1 full reference.
- `../shared/element-tagging.md`, `@coach` tag if the same trainer
  needs to appear consistently across multiple supporting shots.
