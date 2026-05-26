# SaaS Feature Demo Starter Pack

> 60-second how-to. Paste a viral SaaS demo URL, get a paste-ready
> Higgsfield rebuild prompt plus a live-capture shot list, hand off
> to your reel assembly skill.

## What this is

A preconfigured Path A intake for SaaS founders, indie hackers, and
micro-SaaS launches. Built on top of `higgsfield-viral-replicator`.
Bakes in the SaaS research from `/tmp/starter-pack-industry-research.md`
section 6: demo-aha cadence (0:00 hook → 0:03 demo → 0:10 result →
0:20 CTA), build-in-public revenue hooks, replace-this-tool hooks,
banned vocab, no-fake-demo rule.

## Use it when

- You see a Marc Lou / ShipFast, Pieter Levels / Photo AI, or other
  indie SaaS reel working and want to replicate the structure
- A founder client wants their "version of that demo reel" and you
  need the cadence right
- You have a winning hook pattern (demo-first, replace-incumbent,
  build-in-public) you want to translate to a new product

## How long it takes

- 5 to 15 minutes per run, end to end
- Roughly 20 to 50 Higgsfield credits per rebuild render (one
  dominant 3 to 5 second cold-open hero shot)
- Plus 1 Apify run for the scrape
- Plus 5 to 15 minutes for the founder to capture the live screen
  recording (Loom or QuickTime, not Higgsfield)

## How to use it (3 steps)

1. **Open `brief.md`** and fill in the six variables
   (`{{BRAND_NAME}}`, `{{HERO_BENEFIT}}`, `{{LOCATION}}`,
   `{{VOICE}}`, `{{INCUMBENT}}`, `{{PRICE_POINT}}`) plus the brand
   context block.

2. **Run the three prompts in `prompts.md` in order**:
   - Prompt 1 deconstructs the viral reference and maps it to the
     SaaS demo cadence (cold open / demo / result / CTA)
   - Prompt 2 rebuilds it for your brand. Generates a Higgsfield
     prompt for the COLD OPEN only, plus a live-capture shot list
     for the screen recording.
   - Prompt 3 writes the handoff note with the live-capture shot list

3. **Hand off** to:
   - `motion-graphic-reels` for default SaaS demos (screen recording
     plus on-screen text plus visual primitives)
   - `cinematic-ai-reels` for founder-selfie build-in-public reels
   - `frontcam-reels` if the founder is filming themselves narrating

## Important: Higgsfield does NOT generate the screen recording

The middle 70% of any SaaS demo reel (the actual product working on
screen) must be captured live in Loom or QuickTime. Higgsfield is
used only for:
- The cold-open hero shot (founder at desk, product close-up)
- Optionally the CTA-close hero shot
- Any B-roll inserts that aren't the product UI

The downstream reel skill (`motion-graphic-reels`) stitches the
Higgsfield hero shot + live screen recording + on-screen text overlays
into the final 20 to 30 second reel.

## Output you'll end up with

```
~/board/_active/viral-replicator-<date>/<creator-handle>-<post-id>/
├── raw-post.json          (Apify scrape of the original)
├── deconstruction.md      (9-section breakdown + SaaS cadence map)
├── rebuild.md             (shot-by-shot table + caption draft +
│                           SCREEN-RECORDING / HIGGSFIELD beat tags)
├── higgsfield.md          (paste-ready prompt for the cold-open shot)
└── handoff.md             (which reel skill + live-capture shot list)
```

## SaaS hard rules (baked into the pack)

- No fake demos. Real clicks, real data, real latency.
- No vague "AI-powered" claims without showing what the AI does.
- Don't gate the demo behind a signup. Show the product working
  in the video itself.
- No corporate enterprise-y language ("synergy", "leverage",
  "best-in-class"). Repels indie/dev buyers.
- Founder face is a trust signal for indie SaaS. Use it.
- Build-in-public reels need real receipts, never fake numbers.
- AU English. No em dashes. No "game-changer", "10x", "next-gen",
  "revolutionary".
- See `brief.md` for the full list.

## Pairs with

- `higgsfield-viral-replicator` (parent skill)
- `motion-graphic-reels` (default SaaS assembly, screen recording
  plus typeset overlays plus visual primitives)
- `cinematic-ai-reels` or `frontcam-reels` (founder-selfie variants)
- `apify-content-analytics` (engagement check on the rebuilt post)
- `content-engine` + `humanizer` (mandatory voice ship-gates)
