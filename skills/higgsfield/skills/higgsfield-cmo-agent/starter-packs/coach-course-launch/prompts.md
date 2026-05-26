# Starter Pack Prompts: Coach / Course Launch

Three paste-ready prompts for the coach / course creator vertical.
Each one drops into the `higgsfield-cmo-agent` pipeline at a specific
stage with the brief in this folder pre-loaded.

Variables in `{{double-braces}}` get filled from `brief.md` (most are
captured at Stage 0 intake). The pipeline reads `brief.md` first, then
applies these prompts to override or extend the default stage prompts
for the coach / course vertical.

---

## Prompt 1: Campaign Skeleton Kickoff (Stage 0 to Stage 1 Dispatch)

Paste this when starting a cohort launch campaign. It loads the
brief, captures the launch-specific variables, and dispatches Stage 1
with coach-vertical priors baked in.

```text
Run higgsfield-cmo-agent using the Coach / Course Launch starter pack
at ~/.claude/skills/higgsfield/skills/higgsfield-cmo-agent/starter-packs/coach-course-launch/brief.md

Capture these Stage 0 variables in one batched ask, then dispatch
Stage 1 immediately:

- Brand / program name ({{BRAND}})
- Coach name, the operator on camera ({{COACH_NAME}})
- Offer ({{OFFER}}) and price ({{PRICE}})
- Cart open ({{CART_OPEN_DATE}}) and cart close ({{CART_CLOSE_DATE}})
- Program kickoff date ({{LAUNCH_DATE}})
- Masterclass / webinar date if applicable ({{MASTERCLASS_DATE}})
- Signature method name ({{METHOD_NAME}})
- Transformation timeframe ({{TIMEFRAME}})
- Hero client result with receipts ({{HERO_RESULT}}), NOT an income
  claim, specific named outcome
- Target avatar in 12 words max ({{TARGET_AVATAR}})
- Niche ({{NICHE}})
- Origin moment if the brand has one ({{ORIGIN_MOMENT}})
- Specific plateau the avatar is stuck at ({{SPECIFIC_PLATEAU}})
- Real cohort seat cap, drives honest scarcity ({{COHORT_CAP}})
- Language: AU or US English ({{LANGUAGE}})
- Email list size + warmth segmentation
- Past affiliate partners to load into the Stage 6 kill list

Then run Stage 1 (Audience Segments) with these coach-vertical priors:

1. Use the operator's chosen language ({{LANGUAGE}}). Default is the
   coach's call, do not auto-pick.
2. Lead with the course-fatigued operator segment, flag as REPEAT
   primary. They are the cohort's anchor buyer.
3. The "almost there" practitioner is the AMPLIFIER, they generate
   the case studies that close cohort 2.
4. Force "Where they live online" to name specific newsletters
   (Justin Welsh's, Dan Koe's, Ship 30), specific YouTube creators,
   specific Twitter circles, specific Skool / Circle / Slack
   communities. NEVER generic "LinkedIn" or "Twitter".
5. Buying trigger must be one specific moment, not "when they're
   ready". Example: "They just delivered their 5th client free-or-
   discounted because their pricing wasn't anchored, the next
   discovery call is in 3 days."
6. Apply the coach ban-list from brief.md: no income claims, no
   "make $X in Y" language, no rented luxury, no fake scarcity,
   no DM-bait CTAs in copy, no "guru" energy.

Output to:
~/board/_active/cmo-agent-{{BRAND_SLUG}}-{{YYYY-MM-DD}}/

Pause after Stage 1 and surface the segments + rejected segments
footer for review before dispatching Stage 2.
```

---

## Prompt 2: Coach Creative Brief Variant (Stage 3 Override)

Paste this when you reach Stage 3 and want the coach-specific
creative brief format. Overrides the default Stage 3 prompt with
coach visual archetypes (talking-head + screen-record-teach +
walking-and-talking) and the receipts-first anchor.

```text
Run Stage 3 of higgsfield-cmo-agent (Creative Briefs) for the
{{BRAND}} {{OFFER}} launch using the coach vertical override.

Read 01-segments.md and 02-channel-plan.md from the campaign output
directory. Write ONE creative brief per segment using the standard
format with these coach-specific anchors:

**Big idea constraint:**
Every big idea names a specific belief the segment holds + the
specific receipts that break it. Not "{{METHOD_NAME}} works". YES
"{{HERO_CLIENT_FIRST_NAME}} stopped doing {{COMMON_BELIEF_THE_NICHE_HOLDS}}
and {{SPECIFIC_OBSERVABLE_CHANGE_WITH_TIMESTAMP}}".

**Insight constraint:**
The insight paragraph names the EXACT moment the segment loses
trust in coach marketing. For the course-fatigued operator, this is
when a coach uses rented luxury or stages a "thinking" pose. For the
"almost there" practitioner, it's when a coach pitches a generic
framework instead of a specific named problem-solution match.

**Visual direction (locked for coach):**
- Setting: home office, co-working space, hotel lobby, walking
  outdoors with phone selfie. NEVER a styled studio. NEVER a rented
  luxury prop.
- Subject: the coach, always. Wardrobe = elevated casual (good t-
  shirt, blazer over tee, no power suit). Optional: real clients on
  testimonial cuts with written permission.
- Lighting: natural window light, warm domestic interior light, or
  ring light for talking-head only when the window light is bad. No
  studio strobes.
- Camera energy: ONE of these per asset type:
  - Talking-head: still cam, mid-shot, leaning slightly in
  - Screen-record-teach: full screen with founder webcam in corner
    (Loom-style), arrows + circles drawn on the framework
  - Walking-and-talking: handheld phone selfie outdoors or hotel
    lobby
- Color palette: pull from the coach's existing brand palette, the
  home office wall, or the framework slide template.
- Product visibility: The coach IS the product. Hero is the coach's
  face. Method framework (whiteboard / slide / Figma frame) is the
  secondary visual hero.

**Voice/copy direction (locked for coach):**
- Tone words: high-conviction, story-led, slightly-fast
- Phrases to use: "Here's what nobody told me about {{NICHE}}",
  "I figured this out after {{NUMBER}} {{ATTEMPTS_OR_YEARS}}",
  "My client {{CLIENT_FIRST_NAME}} did {{SPECIFIC_THING}} and
  {{SPECIFIC_RESULT}}", "Watch what happens when you {{ACTION}}
  instead of {{COMMON_BELIEF}}", "I built {{METHOD_NAME}} because
  {{ORIGIN_PAIN}}"
- Phrases banned: "make $X in Y", "passive income", "guaranteed
  results", "limited spots" without real cap, "DM me 'INFO'" in
  copy, "quit your 9 to 5", "Wolf of Wall Street" anything, "secret
  sauce", "unlock", "elevate", "transform", any em dash.

**Do (coach-specific):**
- Lead with a specific named client result with receipts (revenue,
  outcome, time-stamp), NOT an income claim about the future.
- Use a specific timestamp ({{HERO_RESULT_DATE}}) when citing a
  client outcome. Receipts have dates.
- Cite the named method ({{METHOD_NAME}}) verbatim in every brief.
- Use a specific number ({{NUMBER_OF_CLIENTS}}, {{TIMEFRAME}},
  {{COHORT_CAP}}) verbatim, not "many" or "a lot".
- Lead with story + receipts for the course-fatigued segment, lead
  with framework-teach for the "almost there" segment.

**Don't (coach-specific):**
- Stage a Tony-Robbins pose at a Miami penthouse.
- Use rented luxury (Lambo, watch close-up, jet selfie).
- Show fake testimonial stacks ("$10K in week 1!" with no real
  client named or dated).
- Pitch with "limited spots" if the cohort cap isn't real.
- Run "DM me 'INFO'" as the CTA, use a free resource URL with a
  real opt-in path instead.
- Use US-coded examples in AU runs, or AU-coded examples in US runs.

**Reference clues (composition only, NOT brand names):**
- A 60-second YouTube long-form thumbnail shot, mid-shot at a home
  desk, coach leaning slightly forward, framework slide visible on
  the wall behind, warm window light.
- A 30-second Reel of the coach walking outdoors mid-sentence, phone
  selfie, hotel lobby behind them, soft natural light.
- A screen-recording teach with the coach's webcam in the corner,
  Notion doc open, the named framework drawn with arrows + circles
  in real time.

**Throughline footer:**
After all per-segment briefs, write the throughline. For coach
launches, the throughline almost always names: (a) the shared
specific plateau every segment is stuck at, (b) the shared visual
anchor (coach + named framework + receipts), and (c) the shared
voice mark (high-conviction story-led with named receipts).

Apply the voice gate (content-engine + humanizer) before saving.
Output to 03-creative-briefs.md in the campaign directory.
```

---

## Prompt 3: Coach Influencer DM Variant (Stage 6 Override)

Paste this when you reach Stage 6 and need coach-tier outreach DMs.
Overrides the default Stage 6 DM template with affiliate / JV /
podcast-swap norms specific to the coach vertical.

```text
Run Stage 6 of higgsfield-cmo-agent (Influencer Army) for the
{{BRAND}} {{OFFER}} launch using the coach vertical DM override.

For each handle in the tier tables (in coach launches, "tiers" map
to: JV partners with overlapping audiences / podcast hosts in the
niche / aligned newsletter operators / Skool + Circle community
founders / past cohort alumni as nano), write a personalised DM
following this coach 5-beat shape with affiliate framing baked in.

Max ~85 words per DM (coach JV partnerships need slightly more
context than cold creator outreach).

**5-beat Coach DM shape:**

1. **Earned opener.** ONE specific thing from their recent content,
   ideally a post or episode adjacent to the program's niche. NOT
   "love your content". YES "Your {{SPECIFIC_RECENT_ASSET}} on
   {{TOPIC}} was the only piece I've read this month that actually
   named {{SPECIFIC_PLATEAU}}".

2. **The program in one specific line.** No CV-dump. ONE sentence
   that names what the cohort does + who it's for + the named
   method. Example: "We run {{OFFER}}, a {{TIMEFRAME}} cohort for
   {{TARGET_AVATAR}} using {{METHOD_NAME}}."

3. **Concrete partnership ask.** Pick ONE of: podcast swap / JV
   affiliate / newsletter mention / co-hosted masterclass / cohort
   alumni guest interview. Format + posting window + audience-fit
   reason. Example: "Would love to swap podcast episodes in the
   {{LAUNCH_WINDOW}} window, your audience overlaps with our
   {{HERO_RESULT_SEGMENT}} cohort by ~{{OVERLAP_GUESS}}%, happy to
   record on your side first."

4. **What's in it for them.** Specific. JV affiliate split + free
   cohort seat for them + reciprocal podcast / newsletter slot.
   NOT "compensation TBD". Example: "30% affiliate on every
   enrolment through your link (typical AOV {{PRICE}}), a free seat
   in the cohort for you if you want to sit in, and a reciprocal
   newsletter feature when we run the next cohort {{NEXT_COHORT_DATE}}."

5. **Easy out.** One line that gives them a clean way to say no.
   Example: "If the cohort's not a fit for your audience or the
   timing's off, totally get it, no follow-up needed."

**Voice rules (coach-specific):**

- No "Hey [first name]!", screams template
- No "we'd love to partner", means nothing
- No "synergy" / "exposure" / "let's hop on a call" before they've
  agreed
- No emojis unless the recipient's voice clearly uses them
- AU or US English to match {{LANGUAGE}} from brief.md
- Direct, peer-to-peer voice. The DM should sound like two coaches
  in the same niche, not "creator pitching brand".
- Sign off with the coach's first name + program tag. Example:
  "{{COACH_NAME}}, {{BRAND}}"

**Format per DM:**

```markdown
### DM: @handle (Tier: [JV-partner/podcast-host/newsletter-op/alumni], Platform: [IG/X/YT/LinkedIn/Podcast])

[Full DM text, ready to send. Max ~85 words. Specific recent-
content reference. Concrete partnership ask. Specific affiliate
split + reciprocal value. Easy out. Coach sign-off.]
```

**Per-handle brief, coach version:**

After the DM, write the standard per-handle brief from the default
Stage 6 prompt, with these coach-specific additions:

- **Partnership type:** Podcast swap / JV affiliate / newsletter
  mention / co-hosted masterclass / alumni interview. PICK ONE.
- **Audience overlap estimate:** What percentage of their audience
  overlaps with the program's ICP. Drives whether the partnership
  is high-value or low-value.
- **Affiliate link / tracking:** Specific affiliate URL or coupon
  code the partner gets. Set the rate now.
- **Receipts to share:** Which client receipts the partner can
  reference in their content. Pre-approve them.
- **Co-content output:** What specific asset the partnership
  produces (1 podcast episode, 1 newsletter feature, 1 IG carousel).

Voice gate (content-engine + humanizer) every DM + every brief
before saving. Then run the GHL + Notion handoffs per the default
Stage 6 flow. Output to 06-influencer-army.md.
```

---

## Notes on Using These Prompts

- Run prompt 1 first. It captures all the launch-specific variables
  and dispatches Stage 1.
- Run prompt 2 only when Stages 0-2 are complete (the brief and
  channel plan must exist for Stage 3 to override sensibly).
- Run prompt 3 only when Stages 0-5 are complete (the social posts
  drive the partnership content angle in Stage 6).
- All three prompts respect the universal ban-list (no em dashes,
  no refund promises, no outcome guarantees) PLUS the coach-
  specific bans (no income claims, no rented luxury, no fake
  scarcity, no DM-bait CTAs).
- The voice gate runs on every stage regardless. Don't skip it.
