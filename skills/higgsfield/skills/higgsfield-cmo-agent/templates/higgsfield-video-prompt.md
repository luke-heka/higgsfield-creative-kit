# Higgsfield Video Prompt: Template (CMO Agent)

Brand-defaulted variant of the canonical video prompt skeleton. When the
campaign brand is **Selr AI**, defaults to AU English, Selr palette, and
the Selr ban-list. When the brand is anything else, falls back to the
generic skeleton in `../shared/higgsfield-prompt-skeletons.md` (Skeleton 2).

Higgsfield's strength is short, motion-forward video. Write prompts that
give a single coherent action per chunk, not a multi-scene narrative.

## Order-Sensitive Skeleton

```
[DURATION + ASPECT], [SHOT TYPE], [SUBJECT + ACTION across the duration],
[SETTING], [TIME OF DAY + LIGHTING], [CAMERA MOVEMENT], [LENS / DEPTH],
[COLOR + TEXTURE], [AUDIO INTENT, optional], [PRODUCT VISIBILITY],
[WHAT TO EXCLUDE]
```

## Hard Rules

1. **Duration: 5-8 seconds per chunk.** Higgsfield works best at this
   range. Do NOT write 30s of action into a 6s clip.
2. **ONE action per chunk.** "Walks to truck and opens tailgate" is one
   thing. "Walks to truck, opens tailgate, then drinks coffee while
   watching sunrise" is three things, pick one.
3. **Name the camera move.** Static / slow push / orbit / dolly out /
   handheld follow / slight drift. "Slight" is your friend, drift, not
   zoom.
4. **Lighting in ONE sentence.** If the lighting plan needs a paragraph,
   the shot is too complex.
5. **Sound (if needed):** describe what audio reinforces ("ambient room
   tone with single Slack ping at second 6, no music"). Omit if not used.
6. **Product visibility EXPLICIT.** Where in frame, for how many seconds.
7. **NO cut/transition language.** "Then it cuts to..." breaks the
   single-action constraint. One scene only per chunk.

## Multi-Chunk Pattern (for posts >8s)

For a 30s Reel:

- Chunk A (0-8s) = hook + setting establishment
- Chunk B (8-16s) = action / tension
- Chunk C (16-24s) = reveal / payoff
- Chunk D (24-30s) = CTA / brand mark

Each chunk = its own Higgsfield prompt. Stitching happens in
post-production (hyperframes / CapCut).

Use `@element` tags to lock product / character consistency across
chunks. See `../shared/element-tagging.md`.

## Field Guide

| Field | Spec | Anti-pattern |
|-------|------|--------------|
| Duration | 5-8s | "10-15s" (too long for one chunk) |
| Aspect | 9:16 / 16:9 / 1:1 | "any" |
| Shot type | medium close-up / wide / over-shoulder / POV | "shot of" |
| Subject + action | specific subject + ONE specific action | multi-action |
| Setting | named location | "outdoors" |
| Lighting | one sentence, direction named | "good lighting" |
| Camera movement | named move + duration | "moves around" |
| Lens / depth | 35-50mm / shallow / mid / deep | "professional" |
| Color + texture | 3 anchor colors + texture cue | "warm" |
| Audio intent | what audio reinforces, or OMIT | "good music" |
| Product visibility | location in frame + duration in seconds | "product visible" |
| EXCLUDE | universal anti-slop + brand-specific | "no bad stuff" |

## Selr AI Defaults (Auto-Inject for Selr Runs)

Identical to image template defaults, see
`higgsfield-image-prompt.md` for the full Selr palette, lighting,
texture, camera, and EXCLUDE block. Video-specific additions:

### Audio defaults (when audio intent specified)

- For workshop B-roll: "ambient workshop room tone with one keyboard
  click or Slack ping at named second, no music"
- For founder talking-head: "founder voiceover natural pace not
  over-acted, no background music or very subtle 60bpm ambient"
- For attendee install reveal: "keyboard clicks then single notification
  ping at named second, no music"

Never: dramatic stinger music, hype drops, "epic" orchestral, US ad-style
voiceover energy.

### Camera movement defaults

- "Slight handheld drift forward over the duration, no zoom"
- "Static medium-wide, no movement"
- "Slow push-in 6 inches over duration, 50mm equivalent"
- Never: whip pan, crash zoom, drone aerial, crane move, dolly track,
  Hollywood-style coverage

### Camera energy defaults

- Handheld with slight natural wobble
- Never tripod-locked perfection (feels staged for AU operator audience)
- Never FPV (wrong energy for B2B operator content)
- Never drone (Selr brand is in-the-room, not above-the-room)

## Worked Example: Selr AI Workshop Reel (Chunk A, 8s)

```
8 seconds 9:16, medium close-up handheld, AU operator man in his early
40s opens his MacBook on a dark wood workshop table and types one line
into a terminal before pressing return as a Slack notification appears
top-right of the screen, in a Selr AI Melbourne workshop room with 11
other operators around tables in soft focus background, mid-morning side
window light natural soft, slight handheld drift forward 4 inches over
the duration no zoom, 50mm equivalent shallow depth of field background
gently out of focus, palette dark wood table (#1A1A1A) cream walls
(#F5F1E8) Selr purple notebook accent (#7B61FF) in lower-right third,
fine film grain natural skin texture, audio: keyboard clicks then single
Slack notification ping at second 6 no music, product visibility: Selr
purple notebook visible in lower-right third for the full 8 seconds,
EXCLUDE: drone shots tripod stability stock-photo poses AI-glossy skin
plastic shine hyper-saturated colors gradient backgrounds drop shadows
emoji watermark overlay text hashtag overlays generic agency aesthetic
neon AI-circuit visuals holographic interfaces "transform" "10x" "next-
level" overlay text US-flag iconography US-centric backdrops dramatic
stinger music hype voiceover crash zoom whip pan.
```

## Worked Example: Selr AI Founder Talking-Head (Chunk A, 6s)

```
6 seconds 9:16, medium close-up handheld, Luke (mid-30s AU founder)
looking directly at the camera and saying one sentence at natural pace
("You don't need another AI course"), in his Gold Coast home office with
a single desk lamp on and bookshelves softly out of focus behind him,
late afternoon side window light warm natural, slight handheld static no
movement, 50mm equivalent shallow depth of field, palette dark wood desk
cream wall Selr purple notebook accent on desk in lower-left, fine film
grain natural skin texture not plastic, audio: founder voiceover natural
direct AU accent no music ambient room tone, product visibility: Selr
purple notebook on desk in lower-left third visible for the full 6
seconds, EXCLUDE: studio lighting tripod-locked perfection drone shots
AI-glossy skin gradient backgrounds drop shadows emoji watermark overlay
text hashtag overlays generic agency aesthetic neon AI-circuit visuals
"transform" "10x" "next-level" overlay text US-flag iconography US-centric
backdrops dramatic stinger music hype voiceover.
```

## Worked Example: Generic Brand (Non-Selr)

For non-Selr campaigns, follow the Stage 3 creative brief's visual
direction. No Selr defaults auto-inject. Universal anti-slop EXCLUDE
still applies:

```
EXCLUDE: AI-glossy skin, plastic shine, hyper-saturated colors, gradient
backgrounds, drop shadows, emoji, watermark, overlay text unless
explicitly requested, hashtag overlays, stock-photography poses, fake
smiles, on-the-nose product hero shots, generic agency aesthetic, cuts
within the clip.
```

## Voiceover-Carrying Chunks (Selr Specific)

For chunks where the founder delivers a verbatim line:

1. Write the EXACT line in the audio field, in quotes.
2. Match chunk duration to spoken line length:
   - 1 sentence ≈ 4-6s
   - 2 sentences ≈ 8-10s (split into 2 chunks if needed)
3. Voice-grade the line through `content-engine` BEFORE locking in.
4. Apply Selr ban-list: no support promises, no outcome guarantees, no
   personal life, no em dashes, no US English.

## Rules Recap

1. **One action per chunk. 5-8 seconds.**
2. **No multi-scene narratives.** Split into multiple chunks if needed.
3. **Use `@element` tags** for product / character consistency across
   chunks.
4. **Audio is optional.** Omit if no spec needed. Don't add hype music.
5. **EXCLUDE block grows.** Add brand-specific anti-patterns to universal
   anti-slop.
6. **AU English in Selr runs.** Spelling distinctions only, model
   vocabulary fields (color, camera, lens) stay as-is.
7. **Voice-grade audio lines BEFORE locking in.** Don't trust your draft.

## Shared Skeleton Reference

Canonical shared skeleton:

```
../shared/higgsfield-prompt-skeletons.md (Skeleton 2)
```

Use this template for CMO-agent runs. Use the shared skeleton directly
when you need a non-brand-defaulted version.

## See Also

- `../shared/higgsfield-prompt-skeletons.md`, canonical Skeletons 1-5
- `../shared/element-tagging.md`, `@product` consistency primitive
- `../shared/negative-constraints.md`, body/motion artifact prevention
- `../shared/hook-bank-100.md`, 100 hooks for opening chunks
