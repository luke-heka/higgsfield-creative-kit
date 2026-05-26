# SaaS Feature Demo: Viral Replicator Brief

> Preconfigured Path A intake for SaaS founders, indie hackers, and
> micro-SaaS launches. Paste a viral reference URL, fill the brand
> block, run `prompts.md`.

---

## Variables (fill these before running)

| Variable | What to put here | Example |
|---|---|---|
| `{{BRAND_NAME}}` | The SaaS product name | ShipFast |
| `{{HERO_BENEFIT}}` | The 10-second aha the demo proves | turn an idea into a live landing page in one click |
| `{{LOCATION}}` | Where the founder ships from | Bali / remote |
| `{{VOICE}}` | Founder voice in 4 to 6 words | honest, dry, slightly nerdy |
| `{{INCUMBENT}}` | The tool this replaces | Notion + Webflow + Zapier |
| `{{PRICE_POINT}}` | MRR anchor for caption | $29/mo or one-time $299 |

---

## Example viral references (real recent posts worth deconstructing)

Pick one. All three map onto the SaaS playbook in
`/tmp/starter-pack-industry-research.md` section 6.

1. **Marc Lou, ShipFast demo-aha reel**
   - URL pattern: `https://www.instagram.com/reel/<reel-id>/` on
     `@marc_louvion` (or his X equivalent) where Marc screen-records
     ShipFast scaffolding an app in 30 seconds with a webcam PIP in
     the corner
   - Why it is worth replicating: this is THE canonical SaaS launch
     format. 0:00 hook → 0:03 demo → 0:10 result → 0:20 CTA. Screen
     recording carries, founder face is trust signal in the corner.
   - Hook archetype expected: claim-then-prove plus demo-aha

2. **Pieter Levels, Nomadlist / Photo AI build-in-public revenue reel**
   - URL pattern: `https://twitter.com/levelsio/status/<id>` or
     `https://www.instagram.com/reel/<id>/` (Pieter selfie + Stripe
     dashboard, "$X MRR in Y days, here is the one feature that did it")
   - Why it is worth replicating: build-in-public revenue hook, real
     receipt, no demo polish, indie-hacker native
   - Hook archetype expected: authority plus receipt-evidence

3. **A "cancel your [incumbent]" reel from any micro-SaaS founder**
   - URL pattern: `https://www.tiktok.com/@<founder>/video/<id>/`
     where a founder calls out a heavyweight incumbent (Notion,
     Calendly, Airtable, ClickUp) and shows their tool doing the same
     job in a fraction of the clicks
   - Why it is worth replicating: replace-this-tool hook, specific
     incumbent named, real diff shown on screen
   - Hook archetype expected: contrarian plus visual-mismatch

> Use real recent posts. The deconstruction reads the actual click
> count visible in the screen recording and the actual on-screen text.

---

## Brand context block (paste this into the rebuild step)

```
Brand: {{BRAND_NAME}}
Category: SaaS / micro-SaaS ({{PRICE_POINT}})
Location: {{LOCATION}}
Founder voice: {{VOICE}}
Hero benefit: {{HERO_BENEFIT}}
Incumbent we replace: {{INCUMBENT}}
Avatar pain: "already pays for 27 SaaS subscriptions, won't add another
  unless it kills one. Won't watch a 5-minute demo. Needs the aha in
  15 seconds. Doesn't trust new tools will exist in 12 months,
  needs to see the founder behind it"
Setting we own: home office, coffee shop, single monitor, hoodie
  (looks like a builder, not a marketer)
Native aesthetic: screen recording with webcam PIP in corner, full-screen
  app demo, real clicks, no fake data, founder voice narrating the flow
Hard bans (from the SaaS research):
  - never fake the demo (r/SaaS and IndieHackers will find out)
  - no vague "AI-powered" without showing what the AI actually does
  - don't gate the demo behind a signup, show the product working
    in the video itself
  - no corporate enterprise-y language ("synergy", "leverage",
    "best-in-class"), repels indie/dev buyers
```

---

## Output reel skill (handoff destination)

For SaaS demos the default handoff is **`motion-graphic-reels`** because
the winning format is screen recording plus typeset on-screen text plus
named visual primitives (browser windows, code blocks, dashboard
overlays). The viral replicator generates a Higgsfield hero shot for
the cold open (the founder at their laptop, or a product close-up),
then `motion-graphic-reels` assembles the full demo with the screen
recording dropped in as the dominant layer.

Override the default to:
- **`cinematic-ai-reels`** if the original was a founder talking-head
  reel with minimal screen recording (Pieter Levels selfie style)
- **`frontcam-reels`** if the actual founder is filming themselves

If `cinematic-ai-reels` is not installed, fall back to `frontcam-reels`
and document the deviation.

> **Important:** Higgsfield is NOT used to generate the screen
> recording itself. The screen recording is captured live (Loom,
> QuickTime, OBS) and dropped into `motion-graphic-reels` for the
> final assembly. Higgsfield is used only for the cold-open hero shot
> and any B-roll inserts (founder at desk, product-on-white close-up).

---

## Voice and style hard rules (SaaS overlay)

These stack on top of the Selr AI house rules in the parent SKILL.md.

- No em dashes. Commas or full stops.
- AU English. Colour, optimise, organise. (Even for global SaaS
  brands shipping from Selr AI's stack, keep AU spelling in captions.)
- Banned vocab (SaaS layer): "synergy", "leverage", "best-in-class",
  "world-class", "next-gen", "revolutionary", "game-changer",
  "AI-powered" (unless followed by a specific demonstrable action).
- No fake demos. Real clicks, real data, real latency visible.
- Founder face in the frame is a trust signal for indie SaaS. Use it.
- Replace-this-tool hooks must show a real diff, not a vibes diff.
- Build-in-public reels must show a real receipt (Stripe screenshot,
  user count, MRR dashboard), never a fake number.
- No "limited spots" or "lifetime deal expires tonight" without a
  real cohort cap and a real date.

---

## Quick demo

```
Deconstruct https://www.instagram.com/reel/<marc-lou-shipfast-recent>/
and rebuild it for {{BRAND_NAME}}. Brand context above. Hand off to
motion-graphic-reels.
```
