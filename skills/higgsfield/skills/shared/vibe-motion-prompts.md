# Vibe Motion Prompt Library (SaaS / UI / Brand Motion Graphics)

Reusable prompt skeletons for Higgsfield Vibe Motion, extracted from real
tutorial workflows (Greg Preece, Zane Hoyer). Vibe Motion generates
deterministic Remotion code, not raster video — text stays crisp, edits are
live, motion is controllable.

Loaded by `higgsfield-marketing-studio`, `higgsfield-ugc-ads`,
`higgsfield-content-factory`, and the `motion-graphic-reels/recipes/saas-explainer.md` recipe.

---

## Prompt Skeleton (every Vibe Motion prompt starts with this)

```
duration N seconds. [aesthetic line]. [background description].
[centered/primary element + animation]. [secondary elements + behaviour].
[cursor behaviour, if any]. [transition keywords if multi-act].
```

Order matters. Vibe Motion parses left-to-right.

---

## Aesthetic Descriptors That Land Reliably

- `editorial minimalist premium`
- `clean white`
- `soft gray lavender gradient`
- `deep navy black background`
- `warm base background throughout`
- `dark serif typography`
- `glass-morphism panels`
- `subtle drop shadow stacked layers`

Avoid invented terms. Vibe Motion silently degrades on unknown style tokens.

---

## Motion Verbs That Work

- `glides in from the right`
- `animates around the ring`
- `swipes onto the screen one by one`
- `fades in line by line`
- `assembling in the center`
- `hard cut to` (forces a two-act mini-animation)
- `hovers over each section in sequence`
- `highlights each one as it goes`

---

## Recipe 1 — Card With Cursor Hover (avatar + headline + CTA button)

```
duration 5 seconds. Clean editorial minimalist premium aesthetic.
Generate a clean white rounded rectangle card assembling in the center of
a soft gray lavender gradient background with stacked glowing shadow layers
radiating outward behind it. On the left of the card, a circular purple
gradient avatar containing the attached headshots. On the right, a bold
content creator heading with smaller gray subtext below. Beneath that, a
wide rounded contact button with a purple to blue gradient and white text.
An arrow cursor glides in from the right and changes to a white pointing
hand when it recovers directly over the center of the button.
```

**Use for:** Reel cover, landing-page hero animation, founder intro card.

---

## Recipe 2 — UI Mockup Hover Sequence (widget + three sections)

```
duration 7 seconds. Generate a clean white widget floating on a deep navy
black background. Inside the widget, there's a title at the top and three
rectangular sections below it, each containing a line of text. Animate a
3D mouse cursor floating in and hovering over each section in sequence,
highlighting each one as it goes.
```

**Use for:** SaaS feature explainer, product demo B-roll, "here's how it
works" mid-reel cutaway.

---

## Recipe 3 — Phone Chat Reveal → Headline Cut (two-act)

```
duration 6 seconds. Warm base background throughout. Editorial minimalist
premium aesthetic. For the first 3 seconds, show a large centered
smartphone chat interface with two messages fading in sequentially. Then,
hard cut to a centered two-line dark brown serif large headline that fades
in line by line.
```

**Use for:** Conversation hook → punchline reveal. Strong opener for IG
reels selling DMs/conversations as a deliverable.

---

## Recipe 4 — Brand Metric Chart (data-driven animation)

```
duration 6 seconds. Gather performance metrics for [BRAND] and animate
them into a chart in the company's brand colors. Show four bars rising in
sequence with the metric label fading in above each bar as it reaches full
height. Background: clean white. Typography: bold sans-serif.
```

**Use for:** Case study reels, "we drove $X for [client]" proof shots,
quarterly recap B-roll.

---

## Recipe 5 — Dashboard Layout Clone (multi-element grid)

```
duration 8 seconds. Generate an animation of a ring. The ring has three
circular widgets evenly spaced animating around the ring. Each widget has
an emoji on it. Now generate a second smaller ring inside of the previous
ring, and this one only has two circular widgets circling around it.
```

**Use for:** Concept visualisation when explaining systems, frameworks,
or relationships. Great for "the 3 pillars of X" content.

---

## Recipe 6 — Brand-Page Clone (UI screenshot mimic)

```
duration 6 seconds. Gather information on the [BRAND] home page. I want
you to build me out a [BRAND] home page with three rows of three video
thumbnails. Each section should have an image for the thumbnail and the
title with a search bar at the top.
```

**Use for:** "Here's what [competitor]'s page looks like" comparison shots
without screenshotting the live site.

---

## Recipe 7 — Product Catalog Swipe-In

```
duration 7 seconds. Animate these three product images like a digital
catalog. Each product should swipe onto the screen one by one. Show the
product name, price, and a key tech or sustainable feature next to each
image. Clean white background, bold sans-serif typography.
```

**Use for:** E-commerce reels, product launch carousels (export frames as
slides), shopping app demo B-roll.

---

## Reference-First Workflow (mandatory for branded animations)

When animating product visuals or brand-specific UI:

1. **Pre-mint references in the Image tab first.**
   - Generate product on white background.
   - Generate brand asset / logo / character.
2. **Switch back to Vibe Motion → Create from scratch.**
3. **Upload references into the References panel.**
4. **Name each reference in the prompt** (e.g. "the attached headshots",
   "the bottle reference").
5. **Vibe Motion then composes** with those exact assets, not
   hallucinated lookalikes.

This is what gives the appearance of "consistency" across animations.

---

## Real-Time Edit Capabilities (post-generation)

After Vibe Motion renders, you can edit live without re-rendering:

- ✅ **Text content** — change a label, price, headline
- ✅ **Color values** — swap hex codes
- ✅ **Element positions** — drag a widget
- ⚠️ **Font weight** — often fails, regenerate instead
- ⚠️ **Element resize** — often fails, regenerate instead

If a real-time edit fails twice, regenerate the whole prompt with the
correction baked in.

---

## Style Switcher

After first render, try the **Legacy style** toggle for an alternative
take on the same prompt. Free option (no extra credit cost) and often
produces a usable variant.

---

## Cost / Failure Budget

Vibe Motion fails ~30-50% of generations on the first try. Budget
accordingly:

- Allocate 1.5× the credits for any campaign-critical animation.
- On failure: read the partial output, identify which element broke,
  rewrite that element clause only.
- Two failures in a row on the same prompt → simplify (drop one
  element, reduce duration).

---

## Caption Generator (post-render)

Vibe Motion can add captions to ANY rendered clip on request:

```
Add captions to this animation. Yellow text, white outline, centred
at bottom. Match the cuts I've already set.
```

Use this for accessibility and feed-without-sound viewing. Cheaper than
generating captions in CapCut for branded animations.
