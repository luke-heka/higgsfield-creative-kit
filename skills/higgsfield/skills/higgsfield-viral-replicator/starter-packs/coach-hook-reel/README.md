# Coach Hook Reel Starter Pack

> 60-second how-to. Paste a viral coach reel URL, get a paste-ready
> Higgsfield rebuild prompt, hand off to your reel assembly skill.

## What this is

A preconfigured Path A intake for online coaches and course creators
(business, mindset, fitness, content). Built on top of
`higgsfield-viral-replicator`. Bakes in the coach research from
`/tmp/starter-pack-industry-research.md` section 5: receipt-first
hooks, direct-to-camera and motion-graphic archetypes, banned vocab,
no-income-promise rules, no-DM-bait CTAs.

## Use it when

- You see a Greg Isenberg, Justin Welsh, Iman Gadzhi, or Hormozi
  reel working and want to replicate the structure for your offer
- A coach client wants their "version of that reel" and you need a
  structural rebuild not a copy
- You have a winning hook pattern (claim-then-prove, authority,
  contrarian) you want to translate to a different niche

## How long it takes

- 5 to 15 minutes per run, end to end
- Roughly 20 to 50 Higgsfield credits per rebuild render (one
  dominant 5 to 8 second hero shot, Skeleton 4 prompt)
- Plus 1 Apify run for the scrape

## How to use it (3 steps)

1. **Open `brief.md`** and fill in the six variables
   (`{{BRAND_NAME}}`, `{{HERO_BENEFIT}}`, `{{LOCATION}}`,
   `{{VOICE}}`, `{{NICHE}}`, `{{SIGNATURE_METHOD}}`) plus the brand
   context block.

2. **Run the three prompts in `prompts.md` in order**:
   - Prompt 1 deconstructs the viral reference into the 9-section
     schema. For Greg-style references it also tags the 7-beat
     skeleton from `gregisenberg-script-formula.md` and the
     motion-graphic primitives from `motion-vocabulary.md`.
   - Prompt 2 rebuilds it for your brand with a paste-ready
     Higgsfield video prompt
   - Prompt 3 writes the handoff note for the downstream reel skill

3. **Hand off** to:
   - `motion-graphic-reels` for Greg-style typography reels
   - `cinematic-ai-reels` for AI-face coach rebuilds
   - `frontcam-reels` if you're filming yourself (Selr AI default)

## Output you'll end up with

```
~/board/_active/viral-replicator-<date>/<creator-handle>-<post-id>/
├── raw-post.json          (Apify scrape of the original)
├── deconstruction.md      (9-section breakdown + Greg 7-beat tag if applicable)
├── rebuild.md             (shot-by-shot table + caption draft)
├── higgsfield.md          (paste-ready prompt for the dominant shot)
└── handoff.md             (which reel skill to load next + why)
```

## Coach hard rules (baked into the pack)

- No income-outcome guarantees. Process language only.
- No rented luxury props. No hotel-lobby flex. No Wolf-of-Wall-Street.
- No "DM me 'INFO'" CTA. Use a real free resource or workshop date.
- No support promises in marketing (no weekly Q&A, no office hours,
  no ongoing helpdesk). Selr AI hard rule.
- AU English. No em dashes. No "game-changer", "10x", "crushing it",
  "secret sauce", "level up", "unlock", "transform", "next-level",
  "guaranteed", "the only way".
- Selr AI specific: no personal-life mixing. Business context only.
- See `brief.md` for the full list.

## Pairs with

- `higgsfield-viral-replicator` (parent skill)
- `motion-graphic-reels` (Greg-style assembly)
- `cinematic-ai-reels` or `frontcam-reels` (direct-to-camera assembly)
- `reels-hook-score` (rank multiple references before rebuilding)
- `gregisenberg-script-formula` (7-beat skeleton reference)
- `content-engine` + `humanizer` (mandatory voice ship-gates)
