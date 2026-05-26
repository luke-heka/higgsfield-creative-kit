# Prompts: SaaS Landing Starter Pack

Three paste-ready Marketing Studio invocations for a SaaS / micro-SaaS / indie tool. Fill the bracketed variables, paste into Claude.

---

## Prompt 1: Cheap Test (2 clips, ~200 credits, ~15 min)

Always run this first. SaaS hooks fail more than DTC because the pain language is abstract. Validate the hook + CTA work before the full stitch.

```
Run higgsfield-marketing-studio cheap_test for this SaaS landing page.

Product URL: <PASTE LANDING PAGE URL>
Goal: conversion
Avatar: custom_mint
Avatar mint prompt: A [26-38] [woman/man], [hair], [skin], wearing
  [hoodie or plain tee], home office or coworking setting, laptop
  visible nearby, soft natural window light, looks like a builder
  not a marketer, slightly nerdy energy, no studio gloss.
Tier: cheap_test
Format mix: UGC (hook 15s) + CTA (5s)
Output folder: ~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/

Voice + style rules (US English, indie-hacker tone):
- No corporate jargon: ban synergy, leverage, best-in-class,
  enterprise-grade, next-generation, cutting-edge, robust, seamless,
  powered by AI.
- No em dashes anywhere (use commas or full stops).
- No outcome guarantees (no "10x", no "save 20 hours per week").
- No banned global vocab: game-changer, 10x, crushing it, killing it,
  secret sauce, level up, unlock, transform.
- Voice = honest, slightly nerdy, no hype. Founder explaining tool to
  a friend on a video call.
- CTA dialogue must pass content-engine + humanizer voice gates BEFORE
  rendering.

If the URL scrape fails (SaaS scrapes fail often, especially Next.js /
Vercel / Cloudflare-gated pages), fall back to manual product entry:
upload hero screenshot + paste name + price + 3 benefit bullets + 100-word
pitch.

Restate intent and wait for my "y" before generating any clip.
```

**Tool params under the hood:**
- product_url: <user URL>
- campaign_goal: conversion
- avatar_mode: custom_mint_from_text
- resolution: 720p
- aspect: 9:16
- clip_count: 2
- formats: [ugc, cta]
- output_dir: ~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/

---

## Prompt 2: Full Stitch (4 clips, ~750 credits, ~45 min)

Run AFTER cheap_test passes. SaaS uses 4 clips (no Unboxing, no Product Review) because physical-product formats kill the native feel.

```
Run higgsfield-marketing-studio full_stitch for this SaaS landing page.

Product URL: <PASTE LANDING PAGE URL>
Goal: conversion
Avatar: custom_mint (same prompt + same locked face as cheap_test)
Avatar mint prompt: <verbatim from cheap_test>
Tier: full_stitch
Format mix:
  - Clip 1: UGC (hook, 15s, role: hook) "If you're still doing [pain] manually..."
  - Clip 2: Tutorial (15s, role: demonstrate) "Here is the old way: [tabs, spreadsheets, Slack]"
  - Clip 3: Demo (15s, role: aha) -> direct Seedance with screen-recording prompt
    (Marketing Studio has no Demo format)
  - Clip 4: CTA (5s, role: action) -> direct Seedance
Resolution: 1080p (all clips)
Output folder: ~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/

Clip 3 Demo prompt skeleton (direct Seedance):
15 seconds 9:16, full-screen screen recording of <tool name> app with
small webcam pip of the founder/avatar in the bottom-right corner, the
cursor navigates through [step 1: open app] then [step 2: paste input]
then [step 3: click the magic button] then [step 4: result appears in
under 2 seconds], voiceover narrating each click in plain English not
corporate, app UI is the real product (not a mockup), clean modern UI,
neutral background, no animated cursors, no synthwave music, ambient
silence with subtle keyboard sounds, EXCLUDE fake UI mockups synthetic
animations corporate stock music

If the real demo cannot be reproduced from Seedance generation (UI too
specific), pause and tell me: I will record a real 15s Loom of the click
flow and we will use that clip instead of an AI generation. This is
non-negotiable, faked demos kill trust in the SaaS market.

CTA dialogue (passed through voice gates before insertion):
"Start the free trial, link below."  (alternatives: "Cancel [incumbent],
link below" / "Try it free for 14 days, no card.")

Hard rules:
- Same avatar locked across clips 1, 2, 4 (webcam pip in clip 3 also
  uses the same face).
- No corporate jargon, no em dashes, no outcome guarantees.
- Speed adjust 80-90% in CapCut for clips 1, 2, 4 (Seedance rushes).
- Demo clip plays at 100% real speed (the click flow IS the proof).
- Caption + on-screen text must pass content-engine + humanizer voice gates.
- Hand final MP4 to higgsfield-ad-critic.

Restate intent and wait for "y" before each clip.
```

**Tool params under the hood:**
- product_url: <user URL>
- campaign_goal: conversion
- avatar_mode: custom_mint_locked
- resolution: 1080p
- aspect: 9:16
- clip_count: 4
- formats: [ugc, tutorial, demo_via_seedance_direct, cta_via_seedance_direct]
- output_dir: ~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/

---

## Prompt 3: CTA-Only Render (1 clip, ~150 credits, ~5 min)

Use when the full_stitch is mostly good but the CTA needs work (wrong incumbent named, weak dialogue, voice tone off).

```
Re-render only the CTA clip for the SaaS campaign at
~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/.

Avatar: same custom_mint locked face from clips 1, 2.
Resolution: 1080p, 9:16, 5s
Engine: Direct Seedance

CTA prompt skeleton:
5 seconds 9:16, medium close-up handheld selfie style, [avatar
description] sitting at a desk with a laptop visible, gesturing toward
an imaginary link below the frame while saying "<CTA dialogue, under 7
words>" with a calm honest expression, home office natural light from a
window behind the camera, handheld with slight wobble no zoom no pan,
50mm equivalent slightly shallow depth of field, neutral palette warm
wood and soft beige natural skin texture not glossy, conversational
honest tone voice clear not rushed, laptop visible in frame,
EXCLUDE em dashes in dialogue hyper-saturated colors plastic AI-glossy
skin corporate stock pose forced smile

CTA copy options (pick one, must pass content-engine + humanizer gates):
- "Start the free trial, link below."
- "Cancel <incumbent>, link below."
- "Try it free, no card required."
- "Link below to try it."

CTA copy gates checklist:
- Under 7 words: y/n
- No outcome guarantee: y/n
- No corporate jargon: y/n
- No em dashes: y/n
- Passes content-engine: y/n
- Passes humanizer: y/n

Save as: <output>/clip-cta.mp4. Re-run the CapCut stitch and ship.
```

**Tool params under the hood:**
- engine: seedance_2.0
- avatar_lock: <slug from full_stitch run>
- duration_s: 5
- resolution: 1080p
- aspect: 9:16
- output_file: <output>/clip-cta.mp4

---

## Run order

1. Prompt 1 (cheap_test) -> hook + CTA validation.
2. Prompt 2 (full_stitch) -> if Demo clip can't be AI-rendered faithfully, pause and record a real Loom for the demo segment.
3. Prompt 3 (CTA-only) if the CTA needs a re-render.

**Hard rule for SaaS:** if the demo cannot be reproduced faithfully via direct Seedance (because the UI is too specific), use a real screen recording. Faked demos are unrecoverable trust damage in the indie/dev market.
