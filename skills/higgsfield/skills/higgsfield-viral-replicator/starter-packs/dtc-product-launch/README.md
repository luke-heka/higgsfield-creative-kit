# DTC Product Launch Starter Pack

> 60-second how-to. Paste a viral DTC reel URL, get a paste-ready
> Higgsfield rebuild prompt, hand off to your reel assembly skill.

## What this is

A preconfigured Path A intake for the DTC ecommerce vertical
(skincare, supplements, apparel, food and bev). Built on top of
`higgsfield-viral-replicator`. Bakes in the DTC research from
`/tmp/starter-pack-industry-research.md` section 1: hook patterns,
visual archetypes, avatar, audio direction, banned vocab,
no-medical-claim rules.

## Use it when

- A DTC brand drops a winning reel you want to replicate for your
  own product line
- A founder asks "can we make our version of that NUDE / OLIPOP
  reel" and you need a structural rebuild not a copy
- You have a viral TikTok Shop pattern (POV pain, ASMR demo,
  founder ingredients reveal) you want to translate to a different
  product

## How long it takes

- 5 to 15 minutes per run, end to end
- Roughly 20 to 50 Higgsfield credits per rebuild render (one
  dominant 5 to 8 second hero shot, Skeleton 4 prompt)
- Plus 1 Apify run for the scrape (free tier covers most cases)

## How to use it (3 steps)

1. **Open `brief.md`** and fill in the six variables
   (`{{BRAND_NAME}}`, `{{HERO_BENEFIT}}`, `{{LOCATION}}`,
   `{{VOICE}}`, `{{PRICE_POINT}}`, `{{AVATAR}}`) plus the brand
   context block.

2. **Run the three prompts in `prompts.md` in order**:
   - Prompt 1 deconstructs the viral reference into the 9-section schema
   - Prompt 2 rebuilds it for your brand with a paste-ready
     Higgsfield video prompt
   - Prompt 3 writes the handoff note for the downstream reel skill

3. **Hand off** to `cinematic-ai-reels` (default) or
   `motion-graphic-reels` (text-only references). The viral replicator
   never auto-fires the downstream skill, the handoff is deliberate.

## Output you'll end up with

```
~/board/_active/viral-replicator-<date>/<creator-handle>-<post-id>/
├── raw-post.json          (Apify scrape of the original)
├── deconstruction.md      (9-section structural breakdown)
├── rebuild.md             (shot-by-shot table + caption draft)
├── higgsfield.md          (paste-ready prompt for the dominant shot)
└── handoff.md             (which reel skill to load next + why)
```

## DTC hard rules (baked into the pack)

- Shot-on-phone vertical 9:16. Never studio, never cinema.
- Product visible from 0:02. Label readable in the final 1.5 seconds.
- No medical-outcome claims. Process language only.
- Customer voice on captions, not brand-marketing voice.
- AU English. No em dashes. No "game-changer", "transformation",
  "revolutionary", "miracle", "clinically proven" without a real study.
- See `brief.md` for the full list.

## Pairs with

- `higgsfield-viral-replicator` (parent skill)
- `cinematic-ai-reels` or `frontcam-reels` (assembly, default DTC)
- `motion-graphic-reels` (assembly, text-only DTC reels)
- `apify-content-analytics` (engagement check on the rebuilt post)
- `content-engine` + `humanizer` (mandatory voice ship-gates)
