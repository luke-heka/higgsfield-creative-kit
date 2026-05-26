# Higgsfield Image Prompt: Template (CMO Agent)

Brand-defaulted variant of the canonical image prompt skeleton. When the
campaign brand is **Selr AI**, defaults to AU English, Selr palette, and
the Selr ban-list. When the brand is anything else, falls back to the
generic skeleton in `../shared/higgsfield-prompt-skeletons.md` (Skeleton 1).

## Order-Sensitive Skeleton

Higgsfield (and most diffusion models) weight earlier tokens more heavily.
Follow this order exactly:

```
[ASPECT RATIO + RESOLUTION], [SHOT TYPE], [SUBJECT and what they're doing],
[SETTING], [TIME OF DAY + LIGHTING], [CAMERA / LENS / DEPTH],
[COLOR PALETTE], [TEXTURE / GRAIN / FILM EMULATION],
[PRODUCT VISIBILITY INSTRUCTION], [WHAT TO EXCLUDE]
```

## Field Guide

| Field | Spec | Anti-pattern |
|-------|------|--------------|
| Aspect ratio | 4:5, 1:1, 9:16, 16:9, match destination surface | "any aspect" |
| Resolution | 2K vertical / 2K horizontal / 4K hero | unspecified |
| Shot type | wide / medium / close-up / over-shoulder / POV / top-down | "shot of" |
| Subject | specific about wardrobe, posture, hands, expression | "a person" |
| Setting | named environment, NOT a vibe | "outdoors" |
| Lighting | golden hour / overcast / hard noon / blue hour / interior practical, name direction | "good lighting" |
| Camera | 35mm full-frame / 50mm portrait / wide handheld / drone + depth (shallow / deep) | "professional camera" |
| Color palette | 3 anchor colors max, hex if known | "any color" |
| Texture | Kodak Portra 400 grain / soft matte / clean digital crisp | unspecified |
| Product visibility | EXPLICIT, location in frame + readability + duration | "product visible" |
| EXCLUDE | brand-specific anti-patterns + universal Selr ban list | "no bad stuff" |

## Selr AI Defaults (Auto-Inject for Selr Runs)

When the campaign brand is Selr AI, append these defaults to every prompt:

### Setting defaults

- For workshop B-roll: "Selr AI workshop room with 12 chairs around 3
  trestle tables, projector, Luke + Harvey at the front, real venue not
  styled set"
- For founder talking-head: "Coworking space side-window or home office
  with one lamp, AU power outlet visible, no styled product flat-lay"
- For attendee B-roll: "Beat-up MacBook on dark wood table, terminal
  visible, Selr purple notebook in lower-third"
- For workshop city establishing: Use the campaign city ("Melbourne",
  "Sydney", "Gold Coast"), never generic

### Color palette default

- `#1A1A1A` (dark wood / table / laptop bezel)
- `#F5F1E8` (cream walls / paper / coffee cup ceramic)
- `#7B61FF` (Selr purple, ACCENT ONLY, never background; appears ONCE
  per frame as notebook spine OR lanyard OR coffee cup edge OR sticker)

### Lighting default

- "Mid-morning side window light, natural soft, overhead fluorescents
  switched off so the room feels human"
- For evening shots: "Late afternoon side light through window, warm
  natural, no studio flash"
- For Office Hours / Skool sessions: "Single desk lamp + screen-glow,
  ambient room dark"

### Texture default

- "Fine film grain, natural skin texture not plastic, no AI shine"

### Camera default

- "Handheld with slight natural wobble, 35-50mm equivalent, shallow
  depth of field"
- For establishing shots: "Static medium-wide, no zoom"
- Never: drone, FPV, tripod-locked perfection, dolly

### Universal Selr EXCLUDE block (append to every prompt)

```
EXCLUDE: stock-photo poses, fake smiles, AI-glossy skin, plastic shine,
hyper-saturated colors, gradient backgrounds, drop shadows, emoji,
watermark, overlay text unless explicitly requested, hashtag overlays,
on-the-nose product hero shots, generic agency aesthetic, neon AI-circuit
visuals, holographic interfaces, "transform" / "10x" / "next-level"
overlay text, US-flag iconography, US-centric backdrops (NYC skylines,
California beach unless campaign specifies)
```

## Worked Example: Selr AI Workshop Reel Frame

```
2K vertical 9:16, medium close-up shot, AU operator man in his early 40s
mid-install on a beat-up MacBook with terminal visible, in a Selr AI
workshop room with 11 other operators around tables in soft focus
background, mid-morning side window light natural soft, 50mm equivalent
shallow depth of field background gently out of focus, palette dark wood
table (#1A1A1A) cream walls (#F5F1E8) Selr purple notebook accent
(#7B61FF) in lower-right third, fine film grain natural skin texture not
plastic, product visibility: Selr purple notebook spine visible in lower-
right third for the full frame label readable not centred, EXCLUDE:
stock-photo poses fake smiles AI-glossy skin plastic shine hyper-
saturated colors gradient backgrounds drop shadows emoji watermark
overlay text hashtag overlays on-the-nose product hero shots generic
agency aesthetic neon AI-circuit visuals holographic interfaces
"transform" "10x" "next-level" overlay text US-flag iconography
US-centric backdrops.
```

## Worked Example: Generic Brand (Non-Selr)

For non-Selr campaigns, follow the Stage 3 creative brief's visual
direction verbatim. No Selr defaults auto-inject. Universal anti-slop
EXCLUDE still applies:

```
EXCLUDE: AI-glossy skin, plastic shine, hyper-saturated colors, gradient
backgrounds, drop shadows, emoji, watermark, overlay text unless
explicitly requested, hashtag overlays, stock-photography poses, fake
smiles, on-the-nose product hero shots, generic agency aesthetic.
```

## Rules

1. **Fill every bracketed field.** If you can't fill one, the Stage 3
   brief is too thin, go back and tighten the brief.
2. **Match aspect ratio to destination surface.** 9:16 for Reel / Story /
   Short / TikTok. 4:5 for IG carousel slide. 1:1 for legacy IG. 16:9
   for YouTube thumbnail / horizontal.
3. **Pick ONE camera energy per prompt.** "Handheld + tripod + drone" is
   no direction.
4. **Product visibility must be EXPLICIT.** Frame location, duration,
   readability. "Product visible" is not a spec.
5. **EXCLUDE block grows.** Add anti-patterns from the Stage 3 creative
   brief's "Don't" list to the universal EXCLUDE.
6. **No em dashes anywhere.** Use commas or full stops.
7. **AU English in Selr runs.** "colour" not "color", but only in the
   parts of the prompt that have spelling distinctions. ("Color palette"
   stays as "color" because it's a technical field name in the model
   vocabulary.)

## Shared Skeleton Reference

This template is the brand-defaulted CMO-agent variant. The canonical
shared skeleton lives at:

```
../shared/higgsfield-prompt-skeletons.md (Skeleton 1)
```

Use this template for CMO-agent runs. Use the shared skeleton directly
when you need a non-brand-defaulted version.

## See Also

- `../shared/higgsfield-prompt-skeletons.md`, canonical Skeletons 1-5
- `../shared/element-tagging.md`, `@product` consistency primitive
- `../shared/negative-constraints.md`, body/motion/anatomy artifact
  prevention
