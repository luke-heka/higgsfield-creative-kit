# Personal Trainer, Content Factory Brief

Preconfigured intake for solo PTs and small-group coaches running 1:1
in-person, online, or hybrid coaching. Built for the AU/NZ market by
default. Edit the variables, leave the structural defaults alone unless
you have data saying otherwise.

---

## Niche (preconfigured)

Solo personal trainer or small-group coach in Australia or New Zealand.
Sells 1:1 in-person sessions ($80-$150 AUD), 10-packs ($750-$1,300 AUD),
online coaching ($150-$400 AUD/mo), or small-group ($40-$60 AUD/session).
Coach is the brand. Customer is the avatar most coaches over-broaden
(busy mum, time-poor exec, lifter who plateaued).

If you're a gym owner running a $39-$99/week membership, use this pack
but swap `training_modality` to `gym_membership` in the variables block.

If you're a registered dietitian, physio, or rehab specialist, pause and
ask for a custom brief, the compliance overlay is different.

---

## Brand voice (PT house voice, not Selr AI)

- Warm and direct. Coachy without yelling.
- Names the client situation in plain language. "Mums who haven't trained
  since the second baby", not "fitness enthusiasts".
- Form-fix tone: precise, not preachy. One cue per sentence.
- Honest about effort. "This is going to feel awkward for two weeks" beats
  "easy 30-day reset".
- AU English. "Programme" not "program", "favourite" not "favorite",
  "kilojoules" or "kJ" when calling out food (not kcal unless your client
  base is US-trained).

---

## Variables to edit

Fill these in before running the factory. Everything in `{{...}}` gets
swapped automatically across the 40 carousels.

```yaml
trainer_name: "{{TRAINER_NAME}}"
business_name: "{{BUSINESS_NAME}}"
location: "{{SUBURB}}, {{CITY}}"        # e.g. "Bondi, Sydney"
training_modality: "{{MODALITY}}"        # 1:1 in-person / online / small-group / hybrid
price_point: "{{PRICE_OR_PACKAGE}}"      # e.g. "$120/session" or "$280/month online"
signature_method_name: "{{METHOD_NAME}}" # e.g. "The Strong Foundation Programme"
client_avatar: "{{CLIENT_AVATAR}}"       # one sentence, the specific person
hero_outcome: "{{HERO_OUTCOME}}"         # the change they actually got, not weight
transformation_timeframe: "{{WEEKS}}"    # e.g. "12 weeks"
common_mistake: "{{COMMON_MISTAKE}}"     # e.g. "half-rep squats"
gym_setting: "{{GYM_SETTING}}"           # own gym / commercial gym / garage / outdoor
booking_link: "{{BOOKING_LINK}}"
language: en-AU
```

---

## Batch size

Default: 5 carousels per batch, 8 batches = 40 carousels over 60 days.

PT calendars often need a faster first run, you can compress to 3 batches
of 5 = 15 carousels over 21 days if you're launching a new programme.
Set `batches: 3` in the brief override before invoking.

---

## Carousel templates per slot

The factory picks templates per idea card. For PTs, the rotation is
weighted toward form-fix education, common mistakes, and real client
transformations (with permission).

| Template | Frequency | When used |
|----------|-----------|-----------|
| `carousel-mistakes` | 30% | "5 mistakes I see in every {{client_avatar}}" |
| `carousel-tips` | 25% | "5 things to do in your first month of training" |
| `carousel-case-study` | 20% | Real client at {{transformation_timeframe}} mark |
| `carousel-myth-bust` | 15% | "Stop believing {{fitness_myth}}" |
| `carousel-cheat-sheet` | 10% | Exercise substitution chart, RPE scale, warm-up flow |

Reel-cover and stack-reveal aren't weighted into the PT rotation, they're
for tool/product reveals, not coaching content.

---

## Industry defaults (don't edit unless you have data saying otherwise)

- **Hashtag pack** (rotated per post): `#{{suburb}}pt`,
  `#personaltrainer`, `#onlinecoach`, `#fitnesstransformation`,
  `#gymtok`, plus one method tag like `#{{method_name}}`.
- **CTA pattern**: "DM the word '{{keyword}}' for the {{lead_magnet}}"
  or "Book a free intro at {{booking_link}}". Never bare "DM me"
  without a keyword, that demotes on TikTok.
- **No weight-loss numbers**: Meta rejects "lose 10kg in 8 weeks" ads.
  Use the non-scale outcome (energy, sleep, confidence, lifting numbers).
- **No body shaming**: never name the viewer's body or habits as the
  problem. Name the situation ("hadn't trained since the second baby"),
  not the person.
- **No shirtless flexing** if female client conversion matters (~70% of
  online coaching market is women), the supporting image prompts in
  `prompts.md` enforce this.
- **Real clients only**: case-study slots need a real before-photo +
  written permission. Don't fabricate transformations.

---

## Kill criteria

Stop the factory and reconfigure if:

- You have no real client transformation to use for any case-study slot.
  Either get one with permission or drop case-study from the rotation.
- You're a registered dietitian / physio / rehab specialist, the
  compliance overlay needs a custom brief.
- You're trying to fill a 60-day calendar before you've trained anyone,
  build a 21-day launch calendar instead (set `batches: 3`).
- Your offer is over $5,000 (high-ticket coaching), use the coach starter
  pack when shipped, the objection set is different.

---

## How to invoke

```
/higgsfield-content-factory personal-trainer
```

Then approve each batch at the gate. The factory will not auto-advance.
