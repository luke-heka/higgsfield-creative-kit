# First 30 Minutes With Higgsfield

You've installed the kit. Higgsfield is wired up. Here's the fastest path from zero to your first piece of branded content.

## Minute 0-3: Confirm everything works

Ask Claude Code:

> *"Use Higgsfield to list the models I can access."*

You should see a list of 30+ models — Soul 2.0, Sora 2, Veo 3.1, Kling, Seedance, Nano Banana, Cinema Studio variants, etc. If you don't, ask Claude to *"check the Higgsfield connection status"* and follow its diagnosis.

## Minute 3-10: Train your Soul ID (if you want a consistent character)

This step is optional for your first piece but **necessary for any series content** where you want the same face across multiple generations. Skip if you only want product-only content.

1. Pick 15-20 photos of yourself (or whoever your brand character is). Multiple angles, clean lighting, no sunglasses, no extreme expressions.
2. Open higgsfield.ai → Characters → Create new Soul ID. Name it something memorable (e.g. `founder-jane`).
3. Upload all photos at once. Higgsfield trains the avatar in ~5 minutes.
4. While it trains, move on to Minute 10.

Full guidance: `docs/soul-id-workflow.md`.

## Minute 10-20: Make your first image

Pick the template that matches your need:

| You want… | Open this template |
|---|---|
| A founder portrait for your About page | `templates/selrai-founder-portrait.md` |
| A hero product shot for your landing page | `templates/selrai-product-hero.md` |
| A behind-the-scenes still for your Story | `templates/selrai-behind-the-scenes.md` |
| A scroll-stopper for an Instagram cover | `templates/selrai-social-carousel-cover.md` |
| Before / after for a transformation | `templates/selrai-before-after-pair.md` |

Then ask Claude Code:

> *"Use the founder-portrait template. Subject: me, in my home office. Lock seed 42."*

Claude reads the template, fills in your specifics, calls Higgsfield, and returns the generated image. If the look isn't right, say *"warmer lighting"* or *"tighter crop"* — Claude reuses the seed and changes one thing.

## Minute 20-30: Make your first video

Same pattern, video templates:

| You want… | Open this template |
|---|---|
| A UGC talking-head ad | `templates/selrai-ugc-talking-head.md` |
| An 8-second ASMR scroll-stopper | `templates/selrai-asmr-scroll-stopper.md` |
| A finished video ad from your product URL | `templates/selrai-click-to-ad-product.md` |
| A trend-jacked Sora 2 piece | `templates/selrai-sora2-trend-template.md` |
| A cinema-grade narrative shot | `templates/selrai-cinema-studio-narrative.md` |

Ask:

> *"8-second ASMR scroll-stopper for my [product] using the asmr-scroll-stopper template."*

Video takes longer to render than images — typically 60-90 seconds for 8s clips, longer for 15-30s pieces. Claude will track the job and tell you when it's done.

## Beyond minute 30 — building the loop

Once you've made one piece in each format, the workflow gets fast:

1. **Lock your Soul ID + winning seed.** Every series uses the same seed for visual consistency.
2. **Make 5-10 variants of your best piece.** Same template, change one variable each time (light, angle, mood, lens).
3. **Pair the visuals with copy.** Pipe the best images/videos to `copywriting` or `direct-response-copy` skill for captions and hooks.
4. **Drop into a carousel.** Use `carousel-generator` skill (or a carousel kit if you've installed that) to render branded multi-slide carousels from your image set.
5. **Strip AI-tone from any captions.** Run captions through `humanizer` or `avoid-ai-writing` skill before publishing.
6. **Publish.** Use `social-content` skill for multi-platform scheduling.

Full pairing playbook: `docs/pairing-with-other-skills.md`.

## What if my generations look wrong?

The cookbook (`docs/cookbook.md`) has a troubleshooting matrix at the bottom that maps common failure modes to fixes. The two most common:

- **Face drifting mid-clip** → train a Soul ID. There's no other fix.
- **Output flat / generic** → you skipped a variable in the MCSLA / 5-variable framework. Add an Action verb and a specific light source.

## What if I want a tool I don't see in the templates?

Ask Claude Code:

> *"What Higgsfield app should I use for <use case>?"*

The bundled prompt skill (`~/.claude/skills/higgsfield/`) has 20 sub-skills covering every model, every camera move, every Soul ID workflow. Claude will route to the right one. Or open the full toolkit map: `docs/full-toolkit-map.md`.

## What if I want to learn more before generating?

Two reading orders:

- **Operator path (just want to ship)**: Read `docs/cookbook.md` once, keep it open in a tab while you work, generate.
- **Director path (want to deeply understand)**: Read the bundled prompt skill at `~/.claude/skills/higgsfield/SKILL.md` and the sub-skills it routes to. That's the full reference. Allow ~2-3 hours for a thorough pass.

Most attendees do the operator path on day 1, then dip into the director path piece by piece as they hit a model or technique they want to master.
