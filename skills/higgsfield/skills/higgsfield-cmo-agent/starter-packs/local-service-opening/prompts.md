# Starter Pack Prompts: Local Service Grand Opening

3 paste-ready prompts for `higgsfield-cmo-agent` runs in the local
service trade + hospo verticals. Drop these into Claude after filling
in the `{{VARIABLES}}` from `brief.md`.

---

## Prompt 1, Stage 0 to Stage 1 dispatch (kickoff)

Paste this to kick off the full 8-stage pipeline using this starter
pack as the brief.

```text
Build me a grand-opening campaign for {{BUSINESS}}, a local {{TRADE_TYPE}} in {{SUBURB}}. Use the local-service-opening starter pack as the Stage 0 brief.

Filled variables:
- Business: {{BUSINESS}}
- Owner: {{OWNER_NAME}}
- Trade: {{TRADE_TYPE}}
- Suburb: {{SUBURB}}
- Street / shopfront (if hospo): {{STREET_NAME}}
- Service radius (if mobile trade): {{RADIUS_KM}} km
- Launch date: {{LAUNCH_DATE}}
- Window: {{LAUNCH_WINDOW}}
- Hero offer: {{HERO_OFFER}}
- Signature offer + price: {{SIGNATURE_OFFER}} at ${{PRICE}}
- Booking link: {{BOOKING_LINK}}
- Hours: {{HOURS}}
- Years in trade: {{YEARS_IN_TRADE}}
- Compliance jurisdiction: AU
- Voice tone pick: {{VOICE_TONE}} (blokey trade / warm hospo / warm personal services)

Run Stage 1 (segments) using the ICP guesses in the brief. Surface 3 to 4 segments with REPEAT or AMPLIFIER or NEITHER flags plus the rejected-segments footer. Stop before Stage 2 and let me confirm segments first.

Voice rules to enforce across the run:
- AU English throughout
- No specific response-time promises
- No phone-only CTAs
- No "best in suburb" claims without proof
- No identifiable customer property in any visual prompt
- No food stock footage in hospo prompts
- Industry ban-list overlay from the starter pack brief applies
```

Expected output: Stage 1 segments file at
`~/board/_active/cmo-agent-{{BUSINESS-slug}}-{{YYYY-MM-DD}}/01-segments.md`.

---

## Prompt 2, Stage 3 creative brief variant for the suburb-local immediate-need ICP

Paste this between Stage 2 (channel plan) and Stage 4 (launch plan)
to generate the creative brief that drives the rest of the visual
prompts.

```text
For Segment 1 (suburb-local emergency / immediate-need buyer), draft the Stage 3 creative brief.

Use the local-service-opening visual archetypes from the brief:
- Trade variant: worksite POV, owner on the tools, problem then fix then clean finish
- Hospo variant: behind-the-counter, hands of the chef plating or pouring, no faces required
- Both: front-of-shop reveal, owner waving on the threshold

Big idea constraint: this segment buys on trust in the first 7 seconds. The creative has to lead with proof of competence (the actual work), not with a brand promise. Trust signals over polish.

Message hierarchy:
1. Problem visible in the suburb (not in a stock kitchen, not in a stock van).
2. Owner-on-site fix or service (real person, branded merch, suburb-named).
3. Booking link + suburb hashtag, never a phone-only CTA.

Visual direction:
- Phone vertical 9:16, no tripods, slight handheld wobble allowed.
- Real worksite or kitchen sound dominant. Voice + ambient only. No corporate music beds.
- For trades, blokey calm voice, no shock-value reveals.
- For hospo, warm stoked voice or no voice (sensory hook).
- Owner persona 30-55, in uniform or branded merch, slight roughness around the edges. NEVER actor-looking.

Hard rules baked into the brief:
- Mask all customer property identifiers (plates, numbers, signage, faces).
- No PPE-missing or unsafe-work footage on trade variants.
- No food stock footage on hospo variants.
- No "best in suburb" claims unless tied to a visible review screenshot in frame.

Output: creative-brief block ready to feed into Stage 5 (social posts).
```

---

## Prompt 3, Stage 6 influencer-army DM variant for suburb-local micro creators

Paste this when running Stage 6 to draft the personalised outreach
DMs. The CMO agent will surface a tiered list, this prompt writes the
suburb-specific DM language.

```text
Draft Stage 6 outreach DMs for the suburb-local micro-influencer list for {{BUSINESS}}.

DM constraints for this vertical:
- AU English. Local voice. Reference the suburb by name in the first sentence.
- 5-beat shape: earned opener (something specific they posted recently in {{SUBURB}}), why we fit (one line on {{BUSINESS}}), concrete ask (free service / first-look invite, NOT a paid post unless they pitched it), what is in it for them (free experience + something newsworthy about the opening), easy out (no obligation to post).
- Max 70 words. Under-promise on what we will give them, over-deliver in person.
- NEVER use the word "collaboration" or "partnership" in the first DM. They are inbox-filtered.
- NEVER offer cash for a first post. Always lead with the free product/service.

DM body for trade-micros (local reno / property / handy-DIY accounts in or adjacent to {{SUBURB}}):
- Earned opener references their recent reno or before-after post.
- Offer = free {{TRADE_TYPE}} job (limited scope, e.g. one room, one fitting, one safety check) at their place or a place they nominate.
- Ask = casual mention or before-after in their grid only if they want to. No script, no brief.

DM body for hospo-micros (local food bloggers + suburb foodie accounts):
- Earned opener references their recent dish or venue review in {{SUBURB}}.
- Offer = open table for them + 1 in opening week, full menu pass.
- Ask = no obligation. If they like it, an honest IG story or short reel is welcome. NEVER request specific copy or hashtags.

DM body for hair/beauty-micros (local lifestyle accounts):
- Earned opener references a recent outfit / look / event post.
- Offer = full first-look cut + colour or signature service on the house in opening week.
- Ask = same casual structure, no obligation.

Output: tiered DM list (5-8 micro per category), each DM personalised on their recent post (use placeholder {{RECENT_POST_REFERENCE}} for the agent to fill from real research in Stage 6 scrape). Include a kill-list footer of 3-5 accounts considered and rejected with reasons (out of suburb, wrong vibe, brand-conflict).
```

---

## Notes on Use

- Run prompts in order: kickoff, confirm Stage 1, kickoff Stage 2,
  paste Prompt 2 for Stage 3, continue Stages 4-5, paste Prompt 3
  for Stage 6, finish Stage 7 + 8.
- All renders downstream of these prompts default to AU English in
  voiceover lines, even if the rest of the campaign assets are
  shipped in mixed language.
- The agent will NEVER auto-send DMs. Stage 6 writes to a Notion page
  with drafted DMs for the owner to review and send manually.
- Compliance overlay (no response-time claims, no fake reviews, no
  customer property reveals) is enforced at every stage's voice-gate
  step, not just at intake.
