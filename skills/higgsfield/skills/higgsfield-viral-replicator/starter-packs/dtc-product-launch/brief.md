# DTC Product Launch: Viral Replicator Brief

> Preconfigured Path A intake for DTC ecommerce (skincare, supplements,
> apparel, food and bev). Paste a viral reference URL into the variables
> below, fill in the brand block, then run `prompts.md` step by step.

---

## Variables (fill these before running)

| Variable | What to put here | Example |
|---|---|---|
| `{{BRAND_NAME}}` | The DTC brand running the ad | NUDE Skin Co |
| `{{HERO_BENEFIT}}` | The one outcome the buyer cares about | clearer skin in 14 days |
| `{{LOCATION}}` | Where the founder or product lives | Byron Bay, NSW |
| `{{VOICE}}` | Founder voice in 4 to 6 words | warm, honest, no marketing polish |
| `{{PRICE_POINT}}` | AOV anchor for caption + CTA | $89 AUD bundle |
| `{{AVATAR}}` | One-sentence buyer profile | 28 to 38 woman, tried three retinols, still has bumps |

---

## Example viral references (real recent posts worth deconstructing)

Pick one. All three are working in 2026 and map cleanly onto the
DTC playbook in `/tmp/starter-pack-industry-research.md` section 1.

1. **NUDE Skin Co founder counter-demo reel**
   - URL pattern: `https://www.instagram.com/p/<post-id>/` (the latest
     reel on `@nudebynature` or `@nudeskinco` showing the cream
     absorbing on the back of a hand)
   - Why it is worth replicating: classic visual demo loop, no cuts,
     ASMR-loud product sound, ends on product label readable
   - Hook archetype expected: claim-then-prove plus visual demo

2. **OLIPOP, Ben Goodwin "what is actually in this can" reel**
   - URL pattern: `https://www.instagram.com/reel/<reel-id>/` on
     `@drinkolipop` (Ben on camera reading the ingredient list)
   - Why it is worth replicating: anti-claim hook, founder on camera
     holding the product, audio-first proof, no studio polish
   - Hook archetype expected: contrarian plus claim-then-prove

3. **TikTok Shop POV pain reel (any top-100 skincare or supps brand)**
   - URL pattern: `https://www.tiktok.com/@<creator>/video/<id>/`
     where a real user posts a "POV: you have tried 5 retinols" reel
     in the bathroom
   - Why it is worth replicating: pure POV pain hook, single bathroom
     setting, soft window light, native phone aspect
   - Hook archetype expected: problem-aware plus story-in-1-sentence

> Picking a real recent post matters. The deconstruction reads the
> ACTUAL engagement signal (saves vs likes vs comments) and the actual
> on-screen text. Don't substitute a stock reference.

---

## Brand context block (paste this into the rebuild step)

```
Brand: {{BRAND_NAME}}
Category: DTC ecommerce ({{PRICE_POINT}} AOV)
Location: {{LOCATION}}
Founder voice: {{VOICE}}
Hero benefit: {{HERO_BENEFIT}}
Avatar: {{AVATAR}}
Setting we own: bathroom counter, kitchen counter, bedside table
  (never studio, never office)
Native aesthetic: shot-on-phone vertical 9:16, soft window light,
  product visible in frame from at least 0:02 onward
Hard bans (from the DTC research):
  - no studio lighting or 4K cinema look
  - no stock B-roll
  - no "shop now" closing card with logo
  - no medical-outcome claims (cures, fixes, treats)
```

---

## Output reel skill (handoff destination)

Default handoff is **`cinematic-ai-reels`**. The winning DTC format is a
real-person face plus real product B-roll. The viral replicator
generates the dominant 5 to 8 second hero shot in Higgsfield, then
`cinematic-ai-reels` stitches the full 20 to 30 second ad with audio
polish and the locked DTC colour grade.

Override to **`motion-graphic-reels`** ONLY when the original reference
was a 100% text-on-screen "before vs after" or "ingredients breakdown"
with no talking head. In that case set `handoff: motion-graphic-reels`
in the handoff note.

If `cinematic-ai-reels` is not yet installed, fall back to
`frontcam-reels` and note the deviation in `handoff.md`.

---

## Voice and style hard rules (DTC overlay)

These stack on top of the Selr AI house rules in the parent SKILL.md.
Apply both.

- No em dashes. Commas or full stops.
- AU English. Colour, optimise, organise.
- Banned vocab (DTC layer): "game-changer", "transformation", "miracle",
  "revolutionary", "secret formula", "clinically proven" (unless a real
  study is cited), "world's best".
- No medical outcome claims. Use process language ("supports", "helps
  with the feeling of", "designed for") not curative claims.
- Customer voice for captions, NOT brand-marketing voice. Texting a
  friend, not pitching a board.
- Founder face in the frame is a trust signal. Use it.
- Product visible by 0:02 in the hero shot, label readable by the
  final 1.5 seconds.

---

## Quick demo

```
Deconstruct https://www.instagram.com/p/<NUDE-recent-post>/ and rebuild
it for {{BRAND_NAME}}. Brand context above. Hand off to cinematic-ai-reels.
```
