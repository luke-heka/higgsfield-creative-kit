# Higgsfield Prompt Skeletons (Image, Video, Carousel-Slide, Rebuild, Testimonial)

Shared field-by-field prompt templates lifted from the Hewitt skills repo
and reconciled with Selr AI house style. Use these as the canonical
starting point for any Higgsfield generation across all sub-skills.

Loaded by every Layer-2 workflow skill.

---

## Skeleton 1 — Image Prompt (order-sensitive)

```
[ASPECT RATIO + RESOLUTION], [SHOT TYPE], [SUBJECT and what they're doing],
[SETTING], [TIME OF DAY + LIGHTING], [CAMERA / LENS / DEPTH],
[COLOR PALETTE], [TEXTURE / GRAIN / FILM EMULATION],
[PRODUCT VISIBILITY INSTRUCTION], [WHAT TO EXCLUDE]
```

### Worked example (UGC character)

```
2K vertical 9:16, medium close-up shot, woman in her early 40s standing
in her modern apartment holding a coffee mug looking at her phone with a
small contented smile, kitchen with warm morning light streaming through
a large window behind her, golden hour 7am lighting natural soft, 50mm
lens shallow depth of field background gently out of focus, warm muted
palette cream and soft brown, fine film grain natural skin texture not
plastic, product not visible in frame, EXCLUDE: stock photography pose
hyper-saturated colors heavy makeup AI-glossy skin gradient backgrounds
emoji overlay watermark
```

### Models this skeleton lands on

- Nano Banana 2 (best for product on white)
- GPT Image 2.0 (best for UGC characters, 2K resolution)
- Soul 2.0 (character consistency, Soul ID locked)
- Seedream (artistic / illustrative styles)
- Flux (high-fidelity realism)

---

## Skeleton 2 — Video Prompt (5-8s, ONE action only)

```
[DURATION + ASPECT], [SHOT TYPE], [SUBJECT + ACTION across the duration],
[SETTING], [TIME OF DAY + LIGHTING], [CAMERA MOVEMENT], [LENS / DEPTH],
[COLOR + TEXTURE], [AUDIO INTENT — optional], [PRODUCT VISIBILITY],
[WHAT TO EXCLUDE]
```

### Worked example (UGC chunk)

```
6 seconds 9:16, medium close-up handheld selfie style, woman in her 40s
holding @bottle and twisting off the cap to tip two capsules into her
palm with a small natural laugh as she does it, modern kitchen warm
morning light, golden hour soft natural lighting, handheld with slight
natural wobble no zoom no pan, 50mm equivalent slightly compressed
shallow depth of field background soft, warm muted cream and brown
palette, audio: natural ambient kitchen sounds her voiceover playing
over: "I started doing this every morning and within two weeks", product
@bottle clearly visible held in hand for 3 seconds then close-up of
palm, EXCLUDE: dolly shots crane shots tripod stability stock-photo
poses overlay text watermark logo bug
```

### Rules

- One action per 5-8s chunk. If you need "picks up bottle AND opens cap AND tips capsules", split into two chunks.
- `@product` tag (see `element-tagging.md`) preserves the exact product across chunks.
- Audio intent is optional — Seedance 2.0 generates dialogue if a voiceover line is provided.

---

## Skeleton 3 — Carousel Slide Image Prompt (mobile-legible)

```
4:5 VERTICAL INSTAGRAM CAROUSEL SLIDE, [SLIDE PURPOSE], visual concept: [...],
typography: [...], layout: [...], color palette: [3 anchors with hex],
texture: [...], imagery (if any): [...], mood: [2 adjectives],
brand cues: [...], EXCLUDE: stock photo people, gradient background,
emoji, drop shadows, hashtag overlays, watermark
```

> **Important for your stack:** Higgsfield-rendered carousel slides
> are **NOT** the preferred path for Selr AI brand carousels. The house
> style is Remotion + Fraunces hand-typeset via `carousel-generator`.
>
> Use this skeleton ONLY for:
> - Slide 4 or slide 7 supporting imagery (background photography)
> - Reel covers that need a single hero image
> - Carousels NOT for Selr AI's own brand (client work, neutral aesthetic)

### Worked example (slide 4 supporting image)

```
4:5 VERTICAL INSTAGRAM CAROUSEL SLIDE, supporting product context for
"here's how to use it", visual concept: laptop on a clean desk with the
Higgsfield interface open in the browser, typography: none — image only,
layout: laptop centered slightly low in frame leaving headroom for
text overlay added later in Photoshop, color palette: #FFFFFF white
desk #1A1A1A laptop bezel #7B61FF subtle purple glow from screen,
texture: clean photographic no grain, imagery: laptop screen showing
Higgsfield Marketing Studio UI faded slightly to avoid overpowering,
mood: focused calm, brand cues: Selr AI purple accent only via screen
glow no logo, EXCLUDE: stock photo people gradient background emoji
drop shadows hashtag overlays watermark
```

---

## Skeleton 4 — Viral Rebuild Prompt (keep mechanic, change surface)

```
[DURATION + ASPECT], [HOOK MECHANIC FROM ORIGINAL], [SUBJECT + ACTION],
[SETTING — DIFFERENT FROM ORIGINAL], [TIME OF DAY + LIGHTING],
[CAMERA MOVEMENT — SAME PATTERN AS ORIGINAL],
[COLOR + TEXTURE — MATCHED TO YOUR BRAND],
[AUDIO INTENT], [PRODUCT VISIBILITY], [WHAT TO EXCLUDE]
```

**Discipline:** keep the original's mechanic (the pattern interrupt, the
camera move, the narrative arc), change the surface (subject, setting,
product, brand voice). Never copy verbatim. Resist on-the-nose
substitution (if original is "sushi chef enters frame at golden hour",
don't rebuild as "insulated cup chef enters frame at golden hour" —
find a different surface for the same mechanic).

### Worked example

Original mechanic: named character enters frame at golden hour, looks
directly at camera, delivers one-sentence promise, walks away.

Rebuild (for Selr AI):

```
6 seconds 9:16, named-character-enters-and-delivers-one-sentence mechanic
(same as reference), the founder walks into a quiet workshop room at end of day,
sets a notebook down on the table looks directly at the camera and says
one sentence about the workshop then walks toward the door, daylight
ambient workshop room, soft late-afternoon window light, slow handheld
push-in 50mm equivalent shallow depth of field, Selr AI palette cream
walls dark wood table single purple notebook accent, audio: ambient
room tone the founder's voice direct and unhurried, product: notebook stays in
frame after the founder walks out, EXCLUDE: drone shots aerial angles stock
office sets gradient overlays text on screen
```

---

## Skeleton 5 — Testimonial Ad Prompt (three discrete treatments)

Each treatment is a discrete choice — pick ONE per quote, don't blend.

### Treatment A — Talking-head reconstruction

AI-rendered "customer" delivers the quote to camera. Must disclose: "Represents a customer profile, not a specific person."

```
5-8 seconds 9:16, talking-head medium close-up, an [AGE] [GENDER] customer-profile
character looking at camera saying the verbatim quote: "[VERBATIM QUOTE]" with a
natural [EMOTION] expression, [CUSTOMER SETTING relevant to the product use case],
ambient natural lighting matching the setting, locked-off slight handheld feel
50mm shallow depth of field, [BRAND-ALIGNED PALETTE], audio: customer voice
clear natural pace not over-acted, product not visible (focus on the person),
on-screen disclosure text "Represents a customer profile, not a specific person"
small bottom corner, EXCLUDE: AI-glossy skin over-acted expressions stock-photo
poses fake-looking smiles
```

### Treatment B — Text-on-B-roll + VO

Quote appears as on-screen text over relevant B-roll, VO reads the quote.

```
5-8 seconds 9:16, [B-ROLL SUBJECT relevant to the product use case], no people
in frame, [SETTING], natural lighting, [CAMERA MOVEMENT — slow push-in or pan],
[BRAND PALETTE], audio: voiceover reads the verbatim quote: "[VERBATIM QUOTE]"
in a calm grounded voice, on-screen text: "[VERBATIM QUOTE — TYPESET IN BRAND FONT]"
appears at the 1s mark stays through 6s fades at 7s, product visibility: subtle
brand element in corner, EXCLUDE: stock B-roll wide-angle distortion harsh edits
```

### Treatment C — Side-by-side before-after

Split-screen or sequential before-after of the customer truth.

```
6-8 seconds 9:16, split-screen vertical, LEFT: [BEFORE STATE — visual] with
muted desaturated palette, RIGHT: [AFTER STATE — visual] with brand palette
restored, both halves locked-off no movement, ambient natural lighting matched
across both, audio: voiceover delivers the verbatim quote: "[VERBATIM QUOTE]"
in calm grounded voice, on-screen text label: "BEFORE" left "AFTER" right
small caps brand font, product visibility: subtle on the AFTER side only,
EXCLUDE: heavy filters over-saturated AFTER stock-style improvement transitions
```

### Universal rules (all three treatments)

- Verbatim quotes only — do not paraphrase customer language
- AI-rendered customer faces require on-screen disclosure
- 5-8s max per spot
- Brand visibility subtle (logo bug max, not overlay)

---

## Anti-Slop Inclusions (every prompt must include these in EXCLUDE)

Append to every Higgsfield prompt's EXCLUDE block, regardless of skeleton:

```
EXCLUDE: AI-glossy skin, plastic shine, hyper-saturated colors,
gradient backgrounds, drop shadows, emoji, watermark, overlay text
unless explicitly requested, hashtag overlays, stock-photography poses,
fake smiles, on-the-nose product hero shots, generic agency aesthetic
```

These suppress the "AI ad" tells that hurt watch-time data.

---

## See Also

- `negative-constraints.md` — body/motion/anatomy artifact prevention
- `element-tagging.md` — `@product` consistency primitive
- `vibe-motion-prompts.md` — Vibe Motion-specific prompt patterns
- `capcut-finishing.md` — post-production fixes after generation
- `hook-bank-100.md` — opening lines for video chunks
