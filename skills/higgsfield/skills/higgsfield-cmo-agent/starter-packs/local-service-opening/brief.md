# Starter Pack Brief: Local Service Grand Opening

> Preconfigured Stage 0 intake for `higgsfield-cmo-agent`. This is NOT a
> Selr AI run. Variables in `{{double-braces}}` are filled by the user at
> kickoff. Everything else is preset for local service trades + hospo.
>
> Source: industry research compiled 2026-05 (Local Service Trade section).
> Voice rules below override the Selr ban-list, this pack uses warm,
> community-first AU-default voice. Trade packs lean blokey/no-bs.
> Hospo packs lean warm/stoked.

---

## Business

- **Business name:** `{{BUSINESS}}` (e.g. "Wholehands Plumbing",
  "Coast & Co Cafe", "The Lane Hair Studio")
- **Trade or category:** `{{TRADE_TYPE}}` (plumber, electrician,
  HVAC, painter, hairdresser, cafe, restaurant, dog groomer, mobile
  mechanic, locksmith, lawn care, cleaner, etc.)
- **Owner / lead operator:** `{{OWNER_NAME}}` (real person on-site, not
  a manager, NOT an actor)
- **Years in trade (or "new opening"):** `{{YEARS_IN_TRADE}}`
- **Voice:** Trade = blokey, no-bs, direct. Hospo + personal services
  (hair, beauty) = warm, stoked, community-first. NEVER agency voice,
  NEVER corporate hold-music tone.
- **Language:** AU English by default (colour, optimise, organise). UK
  + NZ override at intake.

## Hero Offer (Grand Opening or Launch Window)

- **Opening / re-opening type:** `{{OPENING_TYPE}}` (new shopfront,
  service-area expansion, new vehicle on the road, new chair/station,
  new menu, new owner takeover, refurb relaunch)
- **Service area / suburb:** `{{SUBURB}}` + service radius
  `{{RADIUS_KM}}` for trades. Single shopfront address for hospo +
  personal services.
- **Hero offer for the opening window:** `{{HERO_OFFER}}` (e.g.
  "free 5-point home electrical safety check first 30 bookings",
  "$10 off first coffee + pastry combo", "$50 off your first cut +
  colour package", "no call-out fee within `{{SUBURB}}` until end of
  month")
- **Window length:** `{{LAUNCH_WINDOW}}` (default 14-28 days)
- **Booking method:** `{{BOOKING_LINK}}` (the online booking page,
  e.g. ServiceM8 / Calendly / Square / Resy / a Linktree). Phone is
  fallback ONLY, NEVER primary CTA.
- **Hours of operation:** `{{HOURS}}` (incl. after-hours availability
  for trades, kitchen close for hospo)

## Positioning One-Liner

`{{ONE_LINER}}`, fill at intake. Stage 0 prompts the user with three
formats to pick from:

1. "Local `{{TRADE_TYPE}}` in `{{SUBURB}}`, `{{YEARS_IN_TRADE}}` years
   on the tools, finally taking on `{{NEW_CAPACITY}}`."
2. "`{{OWNER_NAME}}` from `{{BUSINESS}}` opens `{{NEW_LOCATION}}` on
   `{{LAUNCH_DATE}}`. Bookings now open."
3. "We're the new `{{TRADE_TYPE}}` on `{{STREET_NAME}}`, and here's
   what's different about how we work."

## Campaign Goal

**Grand opening + community awareness.** Build a 14-28 day window of
inbound bookings, populate Google Maps + Apple Maps presence, light up
the TikTok Local Feed (launched Feb 2026, location-based discovery),
and earn the first 20-50 real-people Google reviews.

- **Anchor metric:** Bookings via `{{BOOKING_LINK}}` in launch window.
- **Secondary metric:** Google Business Profile / Apple Maps verified
  reviews count by `{{LAUNCH_DATE}}` +30 days.
- **Tertiary metric:** TikTok Local Feed video views from inside the
  `{{SUBURB}}` geofence, plus IG saves on opening-week posts.

## ICP Guesses (To Validate in Stage 1)

The Stage 1 prompt will narrow these. Typical local-service segment
shapes:

1. **Suburb-local emergency / immediate-need buyer**, REPEAT primary.
   Search-led (Google + Apple Maps). Needs to trust you on first
   contact. For trades = burst pipe, sparks, no hot water. For hospo
   = walking past, deciding now. Highest-intent, fastest conversion.
2. **Suburb-local discovery buyer**, AMPLIFIER. Scrolling locally on
   TikTok / IG / Facebook Local. Saves the post or follows the page.
   Books in 2-21 days. Drives the word-of-mouth flywheel that feeds
   segment 1.
3. **Adjacent-suburb curious buyer**, NEITHER. Sees the opening post
   from outside `{{RADIUS_KM}}`. Won't convert this launch but
   builds awareness for the next service-area expansion. Don't spend
   paid budget chasing this segment in the opening window.

## Channel Emphasis (Local Service Default)

Stage 2 builds the channel plan. Defaults for this vertical:

- **Primary:** TikTok (Local Feed since Feb 2026 is the highest-leverage
  free distribution for local trades + hospo), Instagram Reels, Google
  Business Profile posts + Q&A + reviews.
- **Secondary:** Facebook local community groups (suburb name + suburb
  buy/swap/sell groups), Apple Maps Business Connect, Nextdoor (US/UK).
- **Tertiary:** Paid Meta within suburb radius for the last week of the
  launch window if anchor metric is short of target. Google LSA (Local
  Service Ads) for trades that qualify.
- **NOT this campaign:** LinkedIn, YouTube long-form, podcasts, email
  list (too small at launch). Saved for month 2+.

## Hero Hooks (3 to pick from for Stage 5 reels)

1. **Satisfying-job-reveal (trades only):** "This is what was actually
   behind the wall in `{{SUBURB}}` this morning." Hands on the work,
   real worksite sound, no music. Voice = blokey, calm, no shock value.
2. **Sensory hospo hook (hospo + personal services):** 2-second
   cheese-pull / milk-pour / blow-dry shine, no words, text overlay at
   3s: "`{{SIGNATURE_OFFER}}`, $`{{PRICE}}`, only at `{{BUSINESS}}` on
   `{{STREET_NAME}}`."
3. **Local-search bait:** "Best `{{TRADE_TYPE}}` in `{{SUBURB}}`?
   Here's how we do `{{SPECIFIC_THING}}` differently." Names suburb in
   first 4 words to win TikTok Local Feed.

## Hard Rules (Compliance + Trust)

- **NEVER promise specific response times** in copy or video voiceover
  ("we'll be there in 30 minutes", "same-day always"). Set the
  expectation in the booking flow, not in marketing copy. Breaking
  this promise once kills the suburb word-of-mouth flywheel.
- **NEVER film identifiable customer property** (street numbers,
  number plates, faces, pets, address signage). Mask everything or
  shoot tight on the work itself. AU consumer rights + privacy.
- **NEVER claim "best in `{{SUBURB}}`" without proof.** If you don't
  have 50+ verified Google reviews to back the claim, drop it. Comes
  off desperate, kills trust.
- **Trades: NEVER film unsafe work** (no PPE, dodgy ladder, live
  circuits exposed). WorkSafe / SafeWork shares it within 48 hours.
- **Hospo: NEVER use food stock footage.** Algorithm hates it, locals
  spot it. Always shot in the kitchen, hands of the actual chef.
- **NEVER offer a phone-call CTA as primary.** Always offer
  `{{BOOKING_LINK}}` or DM-to-book first. Phone is fallback line 2-3.
- **NEVER use review-grouping fake claims** ("5-star service",
  "award-winning") without the actual review screenshot or award
  pictured in frame.
- **AU English** throughout (colour not color, organise not organize,
  centre not center). Hard rule.

## Common Variables to Fill at Intake

- `{{BUSINESS}}`, business name
- `{{OWNER_NAME}}`, real on-site owner / lead tradie / lead chef
- `{{TRADE_TYPE}}`, specific trade or category
- `{{SUBURB}}`, primary suburb name (drives Local Feed targeting)
- `{{STREET_NAME}}`, for hospo + shopfront services
- `{{RADIUS_KM}}`, service area radius for mobile trades
- `{{LAUNCH_DATE}}`, opening day
- `{{LAUNCH_WINDOW}}`, opening campaign length, default 14-28 days
- `{{HERO_OFFER}}`, the specific opening-window offer
- `{{SIGNATURE_OFFER}}`, the lead dish / lead service / lead job-type
- `{{PRICE}}`, typical price band for the signature offer
- `{{BOOKING_LINK}}`, primary online booking URL
- `{{HOURS}}`, opening hours, incl. after-hours availability if any
- `{{YEARS_IN_TRADE}}`, owner's years on the tools (trades) or in
  industry (hospo)
- `{{COMPLIANCE_JURISDICTION}}`, AU / NZ / UK / US for legal voice
  and review-language rules
- `{{NEW_CAPACITY}}`, what's new about this opening (extra van,
  second chair, second shopfront, kitchen takeover)

## Voice Ban-List Stack (Industry Overlay)

In addition to the parent SKILL.md house rules, this pack hard-fails on:

- "Best in the business", "premier", "elite", "world-class",
  "industry-leading", "second-to-none".
- "Family-owned-since-`{{YEAR}}`" claims unless `{{YEAR}}` is real and
  the family is still operating. Caught once, kills trust forever.
- Specific response-time promises ("30-minute response", "same-day
  guaranteed"). Move to booking flow expectations only.
- Phone-only CTAs ("call us now", "ring the office"). Always pair with
  the booking link.
- "We treat your home like our own." Cliche, dead phrase, used by
  every tradie since 2014. Replace with a specific job-finish ritual
  (e.g. "we vacuum before we leave").
- "Family of services" / "trusted partner" / "your local experts".
  Corporate fillers, don't land in suburb voice.

## What This Pack Will Produce in the 8-Stage Run

After running `higgsfield-cmo-agent` with this brief, expected output:

- Stage 1, segments → 3-4 segments per ICP above, REPEAT/AMPLIFIER
  flags, rejected segments footer
- Stage 2, channel plan → TikTok Local Feed + IG Reels + Google
  Business Profile + Facebook local groups, per-segment slot
- Stage 3, creative briefs → owner-on-site visual archetype, blokey or
  warm voice direction per category, compliance kill criteria
- Stage 4, launch plan → 4-week rollout, week 1 = teaser, week 2 =
  opening, weeks 3-4 = social proof from real bookings
- Stage 5, social posts → 5-8 reels per segment, each with caption +
  Higgsfield video prompt + suburb-specific hashtag pack + booking-link
  CTA
- Stage 6, influencer army → local micro-influencers (suburb food
  bloggers for hospo, local reno/property accounts for trades, local
  lifestyle accounts for hair/beauty). NO macro-creators. NO
  out-of-area accounts. AU/NZ/UK + suburb-tagged only.
- Stage 7, aggregated Higgsfield prompts → paste-ready stack of every
  Stage 5 + 6 visual prompt
- Stage 8, GHL + Notion handoff → tagged contacts for the influencer
  outreach list, a Notion campaign page with DMs drafted but
  NEVER auto-sent

## Out of Scope (For Stage 0)

- Loyalty / referral program design (month 2+ work)
- Email list nurture (no list yet at launch)
- Long-form YouTube or podcast (wrong channel for opening window)
- Paid LinkedIn (wrong audience for local services)

## Hand-off Verification

Stage 0 ends when the user confirms:

- All `{{VARIABLES}}` filled, no double-braces remain
- `{{BOOKING_LINK}}` resolves to a real booking page (not a generic homepage)
- `{{SUBURB}}` is the actual targeting suburb, not a city name
- Voice tone picked: blokey trade / warm hospo / warm personal
- Compliance jurisdiction confirmed
- No phone-only CTA in the brief
