# Stage 0: Brief Capture

Goal: Capture every input needed for Stages 1-7 in one batch. Two paths
depending on whether the user said "for Selr AI" or named another brand.

## Path A: Selr AI Auto-Load (SHORTCUT)

If the user said any of:

- "for Selr AI"
- "for Selr"
- "use Selr defaults"
- "Selr AI workshop campaign"
- "my brand"

Skip the intake interview. Auto-load defaults and ONLY ask the user the
4 short questions that vary per campaign.

### Defaults to load (from disk)

Read these files and pull the named fields:

1. `~/.claude/projects/-Users-luke/memory/selrai-business-model.md`
   - Hero offers and pricing
   - Positioning one-liner
   - Voice + tone defaults
   - Team roles + delivery rhythm
2. `~/.claude/projects/-Users-luke/memory/brand-contact-urls.md`
   - IG handles (@selr__ai, @mr_heka)
   - YouTube channel (@mr_heka)
   - Workshop landing URL (workshop.selrai.com.au)
   - Short-link domain (link.selrai.com.au, NEVER in footers)

### Per-campaign questions (ask in one batch)

```
For the Selr AI campaign, four quick questions:

1. Which offer is the campaign for? (workshop / Skool Premium /
   AI Systems Architecture / High-end Consulting / Strategy Call)
2. If workshop, which city? (Gold Coast / Melbourne / Sydney / other)
3. Campaign goal? (registrations / Skool conversions / ASA pipeline /
   strategy call bookings / brand awareness)
4. Date window? (e.g. "next 4 weeks ending on the Melbourne workshop date
   2026-06-12")
```

### File to write (`00-brief.md`)

```markdown
# Campaign Brief: Selr AI, <campaign descriptor>, <YYYY-MM-DD>

> Brand defaults auto-loaded from selrai-business-model.md +
> brand-contact-urls.md. Per-campaign fields captured from user.

## Brand

- **Name:** Selr AI
- **Category:** AI implementation + community for AU SMB operators and AI
  practitioners
- **Voice:** Confident, direct, AU English, no hype. Operator talking to
  operator.
- **Language:** AU English (colour, optimise, specialise, organisation).
- **Hard bans (Selr ban-list):** support promises, outcome guarantees,
  drop-in invites, personal life in marketing, refund promises, em dashes,
  US English.

## Offers

- **In-person Workshop**, $1,500 AUD, full day, max 12 attendees, one
  city per month rhythm (Gold Coast / Melbourne / Sydney).
- **Online Standard**, $499 AUD, self-paced.
- **Skool Premium**, $499/mo USD, 3-month lock-in, 5-phase upward
  pricing trajectory. Never bundled.
- **AI Systems Architecture (ASA)**, from $5K AUD, scoped per
  engagement up to $50K+. One-off on-site AI rollout. No retainer.
- **High-end Consulting**, Bespoke, sales-led, premium AU clients only.
- **Strategy Call**, $1,500 AUD.

## URLs

- **IG (brand):** https://instagram.com/selr__ai
- **IG (personal):** https://instagram.com/mr_heka
- **YouTube:** https://youtube.com/@mr_heka
- **Workshop landing:** https://workshop.selrai.com.au

## This Campaign

- **Offer:** <captured from user>
- **City (if workshop):** <captured>
- **Goal:** <captured>
- **Date window:** <captured>
- **Cycle length:** 4 weeks (1 week pre-launch, 1 week launch, 2 weeks
  sustain/optimise)

## ICP Defaults (Selr AI)

1. AU SMB operators (5-50 staff), trades, hospitality, professional
   services. Buying trigger: a recurring ops bottleneck that costs them
   a hire or a weekend.
2. Solo founders building agencies / consultancies on AI. Buying trigger:
   they've built a few automations but can't price the work.
3. Mid-career operators repositioning into AI roles. Buying trigger: their
   current role is shrinking and they need a transition narrative.
4. Regional / hospitality / trades variant, same as #1 but with stronger
   weighting toward in-person credibility and case studies, not online
   credentials.

## References (visual + voice)

- **Visual:** Selr purple (#7B61FF) as accent only, otherwise muted cream
  + dark wood + natural light. Founder-talking-head + workshop B-roll +
  product UI screenshots. No stock photography. No gradient backgrounds.
- **Voice references:** Selr's own carousel-generator output style;
  Luke's verbatim DMs from the Skool community; the workshop close script
  ("Skool is what comes after today").
- **Voice anti-references:** Instagram-fitness brands, agency-pitch decks,
  US influencer-coach scripts.
```

## Path B: Generic Brand (Full Intake)

If the brand is NOT Selr AI, run the full intake interview in one batch.

### One-batch interview prompt

```
Quick batch to capture the brief, answer in whatever depth you want for
each:

1. Brand name (or "skip, invent one")
2. Hero product or service + price band
3. One-line positioning
4. Best guess at ICPs (1-3, we'll validate)
5. Campaign goal: awareness / launch / repositioning / retention / direct
   conversions
6. Tone or visual references (URLs, brands you like the look of, or
   "no opinion")
7. AU or US English (default US unless you say otherwise)
8. Hard exclusions, visuals, channels, claims, language to avoid

If you've dropped a brand brief into the conversation (URL, doc, paragraph)
say "use the brief above" and I'll skip the interview.
```

### File to write (`00-brief.md`)

```markdown
# Campaign Brief: <Brand>, <YYYY-MM-DD>

## Brand

- **Name:** <captured>
- **Category:** <captured>
- **Voice:** <captured or inferred from references>
- **Language:** <AU / US, default US>
- **Hard bans (universal):** em dashes, refund promises in any brand.
- **Hard bans (this brand):** <captured from user>

## Offer

- **Hero product/service:** <captured>
- **Price band:** <captured>
- **Positioning (one line):** <captured>

## ICP Guesses (to validate in Stage 1)

1. <captured>
2. <captured>
3. <captured>

## Campaign

- **Goal:** <captured>
- **Date window:** <captured or "open">
- **Cycle length:** 4 weeks default unless user says otherwise

## References

- **Visual:** <captured>
- **Voice:** <captured>
- **Anti-references:** <captured>

## Existing Assets

- <user lists what's available, photos, video, copy, audience size>
```

## Rules

- Stage 0 is the SOURCE OF TRUTH for Stages 1-7. Every later stage re-reads
  this file.
- Do not fabricate any field. If the user didn't answer, leave the field
  empty and surface the gap to them before running Stage 1.
- For Selr AI runs, hard-default to AU English and the Selr ban-list. Do
  not let later stages override.
- This stage does NOT get voice-graded, it's factual capture. The voice
  gate kicks in at Stage 1.
- Time-box: 60 seconds for Selr auto-load + 4 questions. 3-5 minutes for
  the generic intake.
