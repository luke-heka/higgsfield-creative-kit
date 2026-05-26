# Fixture, Kallaway Viral IG Post (Path A Deterministic Fallback)

> Used when BOTH the Apify Instagram scraper AND `agent-browser` are
> blocked on the live post. Allows the Path A deconstruction step to
> run deterministically for on-camera demos and offline rebuild testing.
> When this fixture is in use, `raw-post.json` is tagged
> `"source": "fixture", "reason": "<scraper block reason>"`.

---

**Source URL:** https://www.instagram.com/p/DAi1lWIPFuB/
**Creator:** @kallaway
**Platform:** Instagram Reel
**Approx. duration:** 8-12 seconds, 9:16 vertical
**Engagement signal:** high, exact numbers vary, used as a "viral
reference" not a benchmark

---

## What it is, in one paragraph

A short kinetic Reel from creator Kallaway delivering a single sharp
insight about modern attention and the creator economy.
Talking-head with stylised cuts, on-screen captions reinforcing the
spoken claim, dense pacing, every second is doing a job. The format
is recognisable: front-loaded provocation, escalating proof, single
payoff line, save-bait.

---

## Key elements (best-effort fixture, verify against the live post if scraping later works)

### Hook (0-2s)

A blunt claim or counter-intuitive statement said directly to camera
with high energy. On-screen caption appears in the first beat to
reinforce the spoken hook for muted viewers.

- **Archetype:** contrarian (most common for Kallaway) or
  claim-then-prove

### Pattern interrupts

Hard cuts every 1-1.5 seconds. Camera angle micro-shifts, framing
tightens. On-screen text changes colour or weight on emphasis words.

- **Cuts per 10s:** ~7-8

### Narrative arc (4 beats)

1. **Claim**, the provocation hits
2. **Why it's true**, 1-2 supporting points
3. **Consequence**, what happens if you ignore it
4. **Directive**, what to do about it (the screenshot-bait)

### Visual style

- **Subject framing:** medium close-up, mostly static frames with cuts
  doing the energy work
- **Camera energy:** static-with-cuts (not handheld, not push-in, the
  cuts ARE the motion)
- **Colour and light:** warm, slightly desaturated grade. Clean room or
  natural setting background, varies by post
- **Cut frequency:** ~7-8 cuts per 10s
- **Style references:** Iman Gadzhi static-with-cuts, Greg Isenberg
  talking-head cadence
- **Typography:** large sans-serif white captions, occasionally an
  emphasis word in a brand accent colour

### Audio role

- **Music:** absent or very low underscore in most posts
- **VO / talking-head:** present, conversational, slightly punchy
- **Diegetic sound:** voice carries everything, no room tone bed
- **Audio's job:** voice IS the rhythm; cuts amplify the rhythm

### Payoff

The screenshot-able single-line directive at the end. Viewer either
saves the Reel or screenshots the on-screen text.

- **Shape:** earned punchline / actionable step
- **Why satisfying:** confirms the viewer's prior belief (identity
  confirmation) AND gives them something to share to look smart

### CTA mechanism

- **Explicit CTA:** sometimes "save this" or "send this to a [role]"
- **Implicit CTA:** save (primary) + screenshot (secondary)

### Why it went viral, hypothesis

Identity-confirmation for the audience (creator-economy operators,
indie founders, attention-economy thinkers). Quotable, save-baited
payoff line. Watch-through is high because the claim escalates and
the payoff is one line.

Mechanics: identity-confirmation + save-bait.

### What's NOT replicable

- Kallaway's specific delivery cadence and on-camera presence
- His existing audience's pre-trust in his POV
- The exact wording of the hook, it's his voice, not yours
- His face (do NOT rebuild as "a different bald creator-economy guy")

---

## Use this fixture when

- The Apify Instagram scraper returns empty or 403
- `agent-browser` hits the Instagram login wall
- You want a deterministic on-stage demo where the deconstruction
  always renders
- You're testing the rebuild prompt offline

---

## What to keep in your rebuild

The MECHANIC, front-loaded provocation + cut-driven pacing +
screenshot-able payoff line. Apply it to your topic and your voice.

Do not mimic:

- The literal subject matter (creator economy, attention)
- Kallaway's specific wording
- Kallaway's face or on-camera presence

---

## Suggested rebuild target

For Selr AI: workshop offer or a "build one AI workflow today" hook.
Talking-head with cuts is on the boundary between cinematic-ai-reels
(real Luke talking-head + AI B-roll on emphasis beats) and
motion-graphic-reels (typeset Luke quote with no face shown).

Default route for Selr AI: **`cinematic-ai-reels`**, real Luke face,
warm grade, cut-driven pacing.

Alternate route: **`motion-graphic-reels`**, if Luke prefers no face,
typeset the contrarian claim as Greg-style Fraunces typography on the
Selr palette.
