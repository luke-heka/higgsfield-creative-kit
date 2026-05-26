# Personal Trainer Starter Pack, Brief

Preconfigured intake for the `higgsfield-ugc-ads` multi-chunk pipeline. This pack ships a 5-chunk mid-funnel-punchy script aimed at a personal trainer or fitness coach selling 1:1 in-person sessions, online coaching, or small-group memberships in Australia.

**How to use:** copy this file to `~/board/_active/ugc-ads-<YYYY-MM-DD>/06-brief.md`, replace every `{{VARIABLE}}` with the trainer's own value, then feed it to the canonical Chat 2 production prompt. The character_lock + universal_directions blocks below are pre-filled to match the gym-floor PT avatar from the research doc.

---

## Variables the owner edits (5 fields, 3 minutes)

| Field | What it is | Example |
|-------|-----------|---------|
| `{{BUSINESS_NAME}}` | Studio / brand name | "Movement Co" |
| `{{TRAINER_NAME}}` | The trainer on camera | "Sarah" |
| `{{OFFER}}` | What you're selling + price anchor | "10-pack 1:1 sessions for $1,200" |
| `{{HERO_BENEFIT}}` | The one outcome in the client's own words | "feels stronger walking up stairs" |
| `{{LOCATION}}` | Suburb + state, for local SEO | "Burleigh Heads, QLD" |
| `{{CLIENT_AVATAR}}` | Who the ad is for | "busy mums in their 30s" or "time-poor tradies" |
| `{{COMMON_MISTAKE}}` | The form / habit you fix that triggers comments | "doing half-rep squats" |
| `{{SIGNATURE_METHOD}}` | Your named method or system | "the Movement Co 12-week build" |
| `{{TIMEFRAME}}` | How long until clients notice change | "first four weeks" |
| `{{BOOKING_URL}}` | DM keyword OR booking page | "DM 'START' or movementco.com.au/start" |
| `{{TRAINER_TAG}}` | Higgsfield Element tag for the trainer | `@trainer` (this is a character tag, not a product tag) |

---

## campaign_name

```
{{BUSINESS_NAME}}, mid-funnel-punchy, 2026-05-26
```

---

## character_lock (gym-floor PT avatar)

```yaml
age: "early 30s"
gender: "female"            # flip per the trainer
appearance: >
  Real-looking personal trainer in her early 30s, candid and natural,
  athletic build but not bodybuilder-extreme, looks like a coach not a
  fitness model. Hair tied back in a low pony, no makeup or very minimal.
  Branded singlet or fitted training tee, training shorts or leggings,
  sneakers. Slight sheen of real sweat is fine. Expression is warm,
  direct, slightly amused, not theatrical.
voice: "Daniel"             # Higgsfield Change Voice, warm direct
soul_id: null
reference_image_path: "01-character-ref.png"
```

If male, rewrite `appearance` with: *"Real-looking male personal trainer in his early 30s, candid and natural, athletic build but not bodybuilder-extreme. Short hair, light stubble allowed, branded training tee, shorts, sneakers. Warm and direct expression, not aggressive coach energy."*

---

## universal_directions (Australian gym-floor aesthetic)

```yaml
hair: >
  Low pony tied back, slightly messy, frizzy ends from real training,
  never fresh-out-of-salon. Same in every chunk.
application: >
  When demonstrating form or holding a piece of equipment, the trainer
  handles it with natural confidence, fingers wrap the bar or kettlebell
  correctly, body position shows actual training knowledge. Eye contact
  with the camera is direct but not intense. No flexing, no gym-bro
  posing.
b_roll: >
  Real Australian gym setting, commercial gym corner with squat racks,
  cable machines, dumbbell rack visible but not the focus. Natural light
  from skylights or large windows where possible, no harsh overhead
  fluoros. Concrete or rubber gym floor visible. Shallow depth of field,
  background gently out of focus. 35mm equivalent (wider than DTC, shows
  the space).
ugc_realism_notes: >
  Selfie handheld or phone-on-tripod-at-bench-height, slight wobble,
  imperfect framing, candid, no studio look. Real ambient gym sound,
  distant clinks of weights, occasional faint music from gym speakers
  but never the dominant track. Trainer breathes naturally between
  sentences, doesn't deliver to camera like a script-read.
```

---

## chunks (5-chunk mid-funnel-punchy)

```yaml
chunks:
  - id: 1
    role: hook
    voiceover: >
      Stop {{COMMON_MISTAKE}} if you actually want results in the
      {{TIMEFRAME}}.
    runtime: 4
    product_tag: null
    framing: >
      Selfie handheld, eye-level, gym rack and weights visible in
      background. Trainer looks directly at lens on the verb "Stop" then
      holds the look through the sentence.
    include_product: false

  - id: 2
    role: problem
    voiceover: >
      Most {{CLIENT_AVATAR}} I see have been training for months and the
      strength just isn't building.
    runtime: 6
    product_tag: null
    framing: >
      Selfie handheld, slight pan to a cable machine or rack behind
      camera, trainer glances at the equipment then back to lens.
      Conversational, not lecturing.
    include_product: false

  - id: 3
    role: solution
    voiceover: >
      What actually works is {{SIGNATURE_METHOD}}, three sessions a week,
      structured around how your week already runs.
    runtime: 6
    product_tag: null
    framing: >
      Trainer stands beside the squat rack and lightly taps the bar,
      casual, no demonstration yet. Camera is steady. Soft confident
      energy, small smile.
    include_product: false

  - id: 4
    role: proof
    voiceover: >
      My client Em came in eight weeks ago, by week four she said it
      felt easier just walking up stairs. That's the {{SIGNATURE_METHOD}}
      doing its job.
    runtime: 8
    product_tag: null
    framing: >
      Static handheld medium shot, trainer leans on the squat rack,
      direct eye contact with lens. Could briefly cut to b-roll of a
      female client doing a goblet squat (separate clip, named real
      client with permission).
    include_product: false

  - id: 5
    role: cta
    voiceover: >
      If you're in {{LOCATION}} and you've had enough of half results,
      {{BOOKING_URL}}.
    runtime: 4
    product_tag: null
    framing: >
      Selfie handheld at chest height, trainer holds eye contact with
      lens, soft smile, no hard-sell energy. Single beat of silence
      after the URL.
    include_product: false
```

---

## final_cta

```yaml
final_cta:
  voiceover: >
    {{BOOKING_URL}}.
  runtime: 4
  on_screen_url: ""           # PT ads usually use DM keyword, leave URL blank
```

---

## Product tag convention

This pack is **character-locked, not product-locked**. The trainer IS the product. Use the `@trainer` Element tag to lock the same trainer across all 5 chunks.

- Pre-render the trainer headshot using GPT Image 2.0: *"Generate a candid and natural photo of an athletic personal trainer in her early 30s standing in a real gym, branded training singlet, hair tied back, direct warm expression."* Save to `01-character-ref.png`, upload to Higgsfield Elements, tag as `@trainer`.
- All 5 chunks keep `@trainer` loaded. There is no off-chunk where you remove the tag (unlike DTC where chunks 1 and 2 have no product).

If you're using a real trainer's face (not a generated avatar), upload a real headshot instead. Soul ID via `higgsfield-soul` is recommended for any trainer doing 4+ ads with the same face.

---

## Compliance rules baked into this brief (read before editing)

- **No specific weight-loss numbers.** This brief never says "lose 10kg in 8 weeks", "drop 15 pounds", "shed body fat fast". Voiceover uses outcome language tied to feeling and capability ("feels stronger walking up stairs", "strength building", "easier to carry the kids"). Meta and TikTok auto-reject ads with specific weight-loss claims.
- **No body shaming.** No "before" framing that calls out current body. No "stop being lazy". No shirtless flex shots if you want female client conversion (which is ~70% of online coaching).
- **AU English default.** This pack defaults to AU spelling (organised, optimise, colour). Voiceover phrasing is Australian-conversational ("had enough of half results", "results in the first four weeks"), not American gym-speak.
- **No outcome guarantees.** "Guaranteed transformation", "money-back" or "results or refund", banned. The proof line names a real client by first name with permission, not a percentage.
- **Real before/afters only.** If you swap in a transformation reel, the client must have signed consent and the timeframe must be true.

---

## Hashtag pack (paste into the caption, not the video)

```
#personaltrainer #{{LOCATION_SLUG}}pt #fitnesstransformation #gymtok #onlinecoach #fitnessmotivation #{{BUSINESS_NAME_NO_SPACES}}
```

`{{LOCATION_SLUG}}` examples: `bondi`, `manly`, `richmond`, `austin`, `denver`. Lowercase, no spaces. Use your closest suburb.
