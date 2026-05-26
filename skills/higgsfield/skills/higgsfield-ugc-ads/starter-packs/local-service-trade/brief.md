# Local Service Trade Starter Pack, Brief

Preconfigured intake for the `higgsfield-ugc-ads` multi-chunk pipeline. This pack ships a 5-chunk mid-funnel-punchy script aimed at a local trade or hospo business (plumber, electrician, cafe, hairdresser, restaurant) in Australia.

**How to use:** copy this file to `~/board/_active/ugc-ads-<YYYY-MM-DD>/06-brief.md`, replace every `{{VARIABLE}}` with the business's own value, then feed it to the canonical Chat 2 production prompt. The character_lock + universal_directions blocks below are pre-filled to match the owner-on-site avatar from the research doc.

---

## Variables the owner edits (5 fields, 3 minutes)

| Field | What it is | Example |
|-------|-----------|---------|
| `{{BUSINESS_NAME}}` | Business name | "Mitchell Plumbing" or "Bean Counter Cafe" |
| `{{OWNER_NAME}}` | The owner / lead worker on camera | "Dave" |
| `{{TRADE_TYPE}}` | The category | "plumbing", "cafe", "salon", "electrical", "restaurant" |
| `{{LOCATION}}` | Suburb + state, primary for local SEO | "Bondi, NSW" |
| `{{SERVICE_AREA}}` | Areas you cover (for trades) OR opening hours (for hospo) | "Eastern Suburbs Sydney" or "Open 6am to 2pm Tuesday to Sunday" |
| `{{SIGNATURE_OFFERING}}` | The dish, the job, the cut, the service that defines you | "smashed avo on sourdough", "blocked-drain unblocks", "balayage colour" |
| `{{PRICE_ANCHOR}}` | Specific price, no vague ranges | "$22", "from $190 call-out plus parts", "$180" |
| `{{USP}}` | The one reason a buyer picks you over the next listing | "same-day callouts", "no booking needed before 10am", "family-owned since 1998" |
| `{{BOOKING_URL_OR_KEYWORD}}` | The CTA, book online OR DM keyword | "DM 'BOOK' or mitchellplumbing.com.au" |
| `{{OWNER_TAG}}` | Higgsfield Element tag for the owner | `@owner` (character tag, not product) |
| `{{ASSET_TAG}}` | Optional secondary tag for the workspace (truck, kitchen, salon chair) | `@truck`, `@kitchen`, `@chair` |

---

## campaign_name

```
{{BUSINESS_NAME}}, mid-funnel-punchy, 2026-05-26
```

---

## character_lock (owner-on-site avatar)

```yaml
age: "late 30s to mid 40s"
gender: "male"              # flip per the owner, hospo skews female-friendly
appearance: >
  Real-looking trade or hospo business owner in his late 30s, candid and
  natural, looks like the actual worker not an actor. Branded polo or
  hi-vis shirt for trades, branded apron or chef whites for hospo.
  Working-hand calluses are fine, slight roughness around the edges
  reads as trust. Hair short and practical, light stubble OK. Warm
  no-bs expression.
voice: "Daniel"             # Higgsfield Change Voice, warm Australian, conversational
soul_id: null
reference_image_path: "01-character-ref.png"
```

For hospo (cafe, restaurant, salon), rewrite `appearance` with: *"Real-looking cafe or salon owner in her late 30s, candid and natural, looks like the actual worker not an actor. Branded apron with brand name visible, hair tied back, no makeup or very minimal. Warm but stoked, hands lightly flour-dusted or holding a tool of the trade."*

---

## universal_directions (Australian on-site aesthetic)

```yaml
hair: >
  Short practical hair (trades) OR low pony slightly messy (hospo),
  never salon-fresh. Same in every chunk.
application: >
  When demonstrating a job or product, the owner handles it with natural
  competence, fingers wrap the tool or plate or cup correctly, body
  position shows actual trade knowledge. Eye contact with the camera is
  direct but unhurried. No infomercial smile.
b_roll: >
  Real Australian on-site setting matching the trade: branded ute for
  trades (Toyota Hilux or Ford Ranger, signwriting visible), inside the
  cafe behind the counter for hospo, salon chair with the mirror behind
  for salons. Natural light from a window or open roller door, no harsh
  studio lights. Workshop/kitchen sounds in the background. Shallow
  depth of field, background gently out of focus. 35mm equivalent.
ugc_realism_notes: >
  Selfie handheld OR phone-on-tripod-on-the-ute-bonnet, slight wobble,
  imperfect framing, candid, no studio look. Real ambient worksite or
  kitchen sound, kettle steam, distant power tool, milk steamer hiss,
  whatever fits the trade. Owner breathes naturally between sentences.
  No script-read tone.
```

---

## chunks (5-chunk mid-funnel-punchy)

```yaml
chunks:
  - id: 1
    role: hook
    voiceover: >
      Best {{SIGNATURE_OFFERING}} in {{LOCATION}}? Here's what makes
      ours different.
    runtime: 4
    product_tag: null
    framing: >
      Selfie handheld or static on the bonnet of the ute, eye-level,
      branded signage or shopfront visible in background. Owner looks
      directly at lens with a confident no-bs expression.
    include_product: false

  - id: 2
    role: problem
    voiceover: >
      Most {{TRADE_TYPE}} mobs in {{LOCATION}} either don't show up or
      they show up and the job's still not right.
    runtime: 6
    product_tag: null
    framing: >
      Static handheld medium shot, owner stands beside the ute or
      counter, glances down at his hands then back to lens. Honest,
      not bitter.
    include_product: false

  - id: 3
    role: solution
    voiceover: >
      We do {{SIGNATURE_OFFERING}} the way it should be done, with
      {{USP}}, and you can see exactly what we charge before we start.
    runtime: 6
    product_tag: "{{ASSET_TAG}}"
    framing: >
      Slight pan as owner gestures to the workspace, truck, kitchen,
      or salon station. {{ASSET_TAG}} (ute, kitchen counter, salon
      chair) is clearly visible. Small smile starts.
    include_product: true

  - id: 4
    role: proof
    voiceover: >
      Yesterday I did a {{SIGNATURE_OFFERING}} for a customer in
      {{LOCATION}}, in and out, sorted, they didn't have to chase me.
      That's how we operate.
    runtime: 8
    product_tag: "{{ASSET_TAG}}"
    framing: >
      Medium close-up, owner demonstrates a real job or plates a real
      dish or styles a real cut, hands working. Voiceover narrates as
      the action plays. Confident, micro-smile at the end.
    include_product: true

  - id: 5
    role: cta
    voiceover: >
      If you're in {{LOCATION}} and you need a {{TRADE_TYPE}} who turns
      up, {{BOOKING_URL_OR_KEYWORD}}.
    runtime: 4
    product_tag: "{{ASSET_TAG}}"
    framing: >
      Selfie handheld at chest height, owner holds direct eye contact
      with lens, soft smile. Workspace visible behind. Single beat of
      silence after the URL or DM keyword.
    include_product: true
```

---

## final_cta

```yaml
final_cta:
  voiceover: >
    {{BOOKING_URL_OR_KEYWORD}}.
  runtime: 4
  on_screen_url: ""           # most local trades use DM keyword or call, leave URL blank unless online booking
```

---

## Product tag convention

This pack uses **two tags**: `@owner` for the character (loaded across all 5 chunks) and `{{ASSET_TAG}}` for the workspace (loaded in chunks 3, 4, 5).

- **Owner tag (`@owner`):** pre-render with GPT Image 2.0: *"Generate a candid and natural photo of a {{TRADE_TYPE}} business owner in his late 30s standing on-site in a real Australian {{TRADE_TYPE}} setting, branded shirt, direct warm expression."* Save to `01-character-ref.png`, upload to Higgsfield Elements, tag as `@owner`.
- **Asset tag (`{{ASSET_TAG}}`):** pre-render the workspace with Nano Banana 2: *"Generate a high-quality render of a [branded Hilux ute / cafe counter / salon chair] in a real on-site setting, no people in frame, natural light."* Save to `00-asset-still.png`, upload to Higgsfield Elements, tag as `@truck` / `@kitchen` / `@chair`.
- Chunks 1 and 2 have `{{ASSET_TAG}}` REMOVED from the Elements panel (only `@owner` loaded). Chunks 3, 4, 5 have BOTH tags loaded.

For hospo, you can skip the asset tag entirely and use just `@owner` if the visual focus is the dish in their hands rather than the counter.

---

## Compliance rules baked into this brief (read before editing)

- **No false response-time promises.** This brief never says "we'll be there in 30 minutes" or "guaranteed same-day". Voiceover uses honest language ("we turn up", "you can see exactly what we charge"). Trades are auto-audited for response-time claims under Australian Consumer Law.
- **No customer-property reveals.** If you swap in a worksite reel (chunk 4), mask plate numbers, street numbers, and any identifiable faces or property markers. No filming inside a customer's home without written consent.
- **No "we're the best in [city]" without proof.** The hook says "best in {{LOCATION}}" as a question, not a claim. If you swap it to a flat claim, you trigger ACL "puffery vs misleading" risk.
- **AU English default.** Mate, ute, mob, sorted, brekkie, brick-and-mortar Aussie phrasing welcome. Spell organise, colour, optimise.
- **No phone-only CTA.** TikTok and Meta both demote call-only CTAs in 2026. The CTA is DM keyword OR online booking URL. Phone number is fine as a secondary mention but not the primary CTA.
- **CASA rules for drone B-roll (trades).** Never use drone footage of customer property without written consent. Stick to your own ute, your own shopfront, your own workshop.

---

## Hashtag pack (paste into the caption, not the video)

```
#{{LOCATION_SLUG}} #{{LOCATION_SLUG}}eats #{{LOCATION_SLUG}}tradies #localbusiness #smallbusiness #foryou #{{BUSINESS_NAME_NO_SPACES}}
```

`{{LOCATION_SLUG}}` examples: `bondi`, `manly`, `richmond`, `austin`. For hospo use `#{{LOCATION_SLUG}}eats`. For trades use `#{{LOCATION_SLUG}}tradies`. Drop whichever doesn't fit.
