# Coach Hook Reel: Viral Replicator Brief

> Preconfigured Path A intake for online coaches and course creators
> (business, mindset, fitness, content). Paste a viral reference URL,
> fill the brand block, then run `prompts.md`.

---

## Variables (fill these before running)

| Variable | What to put here | Example |
|---|---|---|
| `{{BRAND_NAME}}` | Coach or course brand | Selr AI (the workshop offer) |
| `{{HERO_BENEFIT}}` | The specific outcome the avatar wants | install a working AI system into your own business in one day |
| `{{LOCATION}}` | Where the coach films from | home office or workshop room |
| `{{VOICE}}` | Coach voice in 4 to 6 words | direct, dry, no hype |
| `{{NICHE}}` | The exact niche the avatar fits | solo business owners stuck on tech setup |
| `{{SIGNATURE_METHOD}}` | The coach's named framework | the one-day AI-ops install |

---

## Example viral references (real recent posts worth deconstructing)

Pick one. All three map onto the coach playbook in
`/tmp/starter-pack-industry-research.md` section 5.

1. **Greg Isenberg, "here is how I" framework reel**
   - URL pattern: `https://www.instagram.com/reel/<reel-id>/` on
     `@gregisenberg` (any recent reel where Greg breaks down a startup
     idea or community-business framework with motion-graphic typography)
   - Why it is worth replicating: this is THE canonical
     coach-meets-motion-graphic format Selr AI already runs through
     `motion-graphic-reels`. The hook is a "here is how I [outcome]"
     line. Beats are 1.5 to 2.5 seconds. Greg never uses an em dash,
     never uses outcome guarantees.
   - Hook archetype expected: claim-then-prove plus curiosity-gap
   - Greg-specific reference: see
     `~/.claude/projects/-Users-luke/memory/gregisenberg-script-formula.md`
     for the 7-beat skeleton this reel will almost certainly use

2. **Justin Welsh, solopreneur 2x2 framework reel**
   - URL pattern: `https://www.instagram.com/reel/<reel-id>/` on
     `@thejustinwelsh` (any recent reel where Justin teaches a 2x2
     matrix or 3-step process to camera, then cuts to text overlay)
   - Why it is worth replicating: pure direct-to-camera coach format,
     bookshelf or branded backdrop, mid-shot, no music, voice carries
   - Hook archetype expected: specific-number plus authority

3. **Iman Gadzhi or Alex Hormozi, "I 2x'd my X" reel**
   - URL pattern: `https://www.instagram.com/reel/<reel-id>/` on
     `@imangadzhi` or `@alexhormozi` (any "here is how I 2x'd my
     conversions without lowering price" reel)
   - Why it is worth replicating: receipt-first hook, calm grounded
     delivery, single setting, no cuts under 1 second
   - Hook archetype expected: contrarian plus authority

> Use real recent posts. Don't substitute a stock reference. The
> deconstruction reads the actual on-screen text and the actual
> engagement signal (saves win for coaches, not likes).

---

## Brand context block (paste this into the rebuild step)

```
Brand: {{BRAND_NAME}}
Category: online coach / course creator
Niche: {{NICHE}}
Location: {{LOCATION}}
Coach voice: {{VOICE}}
Hero benefit: {{HERO_BENEFIT}}
Signature method: {{SIGNATURE_METHOD}}
Avatar pain: "tried 3 other programs, didn't finish, doesn't trust they
  will finish this one. Suspicious of gurus. Wants the specific
  shortcut, not generic info they could Google"
Setting we own: workshop room, home office, bookshelf backdrop, walking
  shot (never rented Lambo, never hotel-lobby flex)
Native aesthetic: mid-shot direct-to-camera, soft natural light,
  one anchor object in frame (notebook, whiteboard, laptop)
Hard bans (from the coach research):
  - never promise specific income outcomes ("make $10K/mo in 30 days")
  - no rented luxury props, no Wolf-of-Wall-Street energy
  - no "DM me 'INFO'" CTA (TikTok demotes DM-bait CTAs)
  - no generic "limited spots" scarcity, use real cohort caps with dates
```

---

## Output reel skill (handoff destination)

For coach reels the dispatcher splits two ways based on the reference's
visual style.

| Reference visual style | Hand off to |
|---|---|
| Greg-style motion-graphic typography (Fraunces text, named visual primitives, no face) | **`motion-graphic-reels`** (Greg-house-style with locked Selr palette) |
| Direct-to-camera coach (Justin Welsh, Iman Gadzhi, Hormozi) | **`cinematic-ai-reels`** for AI face rebuild, OR **`frontcam-reels`** if the coach is filming themselves |
| Mixed (face plus motion-graphic overlays) | **`cinematic-ai-reels`** primary with motion-graphic primitives layered (fallback to `frontcam-reels` plus `motion-graphic-reels`) |

Selr AI default: Luke films himself, so for any Selr AI rebuild route
to **`frontcam-reels`** with a `motion-graphic-reels` overlay pass.

---

## Voice and style hard rules (coach overlay)

These stack on top of the Selr AI house rules in the parent SKILL.md.

- No em dashes. Commas or full stops.
- AU English. Colour, optimise, organise.
- Banned vocab (coach layer): "game-changer", "10x", "crushing it",
  "killing it", "secret sauce", "level up", "unlock", "transform",
  "next-level", "the only way", "guaranteed".
- No outcome guarantees. Process language only ("walk you through
  how to install", "see how the system runs"), never "you will get X
  result by week 4".
- No support promises in marketing copy (no "weekly Q&A", no
  "office hours", no "ongoing helpdesk"). Selr AI hard rule.
- No refund promises anywhere.
- Hooks come from receipts (real client outcome, real revenue, real
  install), not from hype.
- Selr AI specific: no personal-life mixing. If the original used a
  family-member story ("my wife asked me…"), substitute a business
  context ("a workshop attendee asked me…", "a client asked me…").

---

## Quick demo

```
Deconstruct https://www.instagram.com/reel/<gregisenberg-recent>/ and
rebuild it for {{BRAND_NAME}}. Brand context above. Hand off to
motion-graphic-reels.
```
