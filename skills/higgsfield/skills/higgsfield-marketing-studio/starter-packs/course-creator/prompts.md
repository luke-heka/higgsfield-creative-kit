# Prompts: Course Creator Starter Pack

Three paste-ready Marketing Studio invocations for a coach or course creator. Warmer voice, story-led, never income-claimy. Fill the bracketed variables, paste into Claude.

---

## Prompt 1: Cheap Test (2 clips, ~200 credits, ~15 min)

Always run this first. The coach category has the highest hook-fail rate of all three starter packs because pain language is subtle and the compliance bar is the strictest.

```
Run higgsfield-marketing-studio cheap_test for this coach / course sales page.

Product URL: <PASTE SALES PAGE URL>
Goal: awareness
Avatar: custom_mint (or soul_id_<coach_name> if you have a Soul ID set up)
Avatar mint prompt: A [28-45] [woman/man], [hair, well-groomed natural],
  [skin], wearing [elevated casual: good t-shirt, blazer over tee, soft
  knit], [home office bookshelf / co-working / hotel lobby / clean desk],
  warm soft natural light, slightly leaning in with engaged friendly
  expression, looks like a friend giving you the unfair advantage, no
  studio gloss, no rented luxury props.
Tier: cheap_test
Format mix: UGC (hook 15s) + CTA (5s)
Output folder: ~/board/_active/marketing-studio-course-<YYYY-MM-DD>/

HARD compliance rules for this pack (non-negotiable):
- NO income claims: ban "$10K/mo", "6-figure", "7-figure", "$X in 30 days",
  any specific revenue number tied to a buyer outcome.
- NO outcome guarantees: ban "guaranteed transformation", "you will
  [outcome]", "results in 30 days", "100% success rate". Use process
  language only.
- NO refund / money-back / satisfaction guarantees.
- NO rented luxury props (no Lambo, no champagne-on-yacht, no helicopter).
- NO fake or unverified client transformations.
- NO urgency manipulation ("limited spots" without a real cap, "price
  goes up tomorrow" unless it does).
- NO drop-in invites ("come say hi", "swing past", "if you're nearby").
- NO casual support promises ("DM me anytime", "weekly Q&A forever").
- NO em dashes.
- NO banned vocab: game-changer, 10x, crushing it, killing it, secret
  sauce, level up, unlock, transform.

Voice tone: warm, story-led, high-conviction. Like the coach is
explaining their obsession to a smart friend at a coffee shop. Not
corporate, not bro-y, not motivational-speaker.

Hook structure for UGC clip (12-word avatar-naming pattern):
"If you've been [doing X] for [time period] and still aren't [non-monetary
outcome], here's why."

CTA dialogue (lead-magnet CTA outperforms direct-sale on coach audiences):
"Comment <KEYWORD> for the free framework." OR "Link in bio for the
case study."

CTA dialogue must pass content-engine + humanizer voice gates BEFORE
rendering. If any compliance rule is at risk, pause and ask me, do not
render at risk.

Restate intent (including the compliance checklist) and wait for my "y".
```

**Tool params under the hood:**
- product_url: <user URL>
- campaign_goal: awareness
- avatar_mode: custom_mint_from_text (or soul_id_<slug>)
- resolution: 720p
- aspect: 9:16
- clip_count: 2
- formats: [ugc, cta]
- output_dir: ~/board/_active/marketing-studio-course-<YYYY-MM-DD>/

---

## Prompt 2: Full Stitch (4 clips, ~750 credits, ~45 min)

Run AFTER cheap_test passes. Coach mix is 4 clips (no Unboxing, no Product Review): UGC + Tutorial + Story + CTA.

```
Run higgsfield-marketing-studio full_stitch for this coach campaign.

Product URL: <PASTE SALES PAGE URL>
Goal: awareness
Avatar: same locked face as cheap_test (custom_mint or Soul ID)
Avatar mint prompt: <verbatim from cheap_test>
Tier: full_stitch
Format mix:
  - Clip 1: UGC (hook, 15s)
      "If you've been [doing X] for [time] and still aren't [non-monetary
      outcome], here's why."
  - Clip 2: Tutorial (framework, 15s)
      Avatar at desk teaches the framework name + the contrarian move.
      "Most coaches do X, I do Y because Z."
  - Clip 3: Story (proof, 15s) -> direct Seedance with narrative prompt
      (Marketing Studio's product_review format works as fallback but
      tends to feel salesy in this category)
  - Clip 4: CTA (5s) -> direct Seedance
Resolution: 1080p (all clips)
Output folder: ~/board/_active/marketing-studio-course-<YYYY-MM-DD>/

Clip 3 Story prompt skeleton (direct Seedance):
15 seconds 9:16, medium close-up handheld selfie style, [avatar
description] sitting at a home office desk warmly recounting a client
story, "[Client first name] came to me 12 weeks ago [stuck pattern in
plain English, no income mention]. Today she [non-monetary
transformation: more confident, clearer on direction, momentum
back]. Here is what we changed." conversational warm tone, slight
pauses, natural eye contact with camera, warm afternoon natural light
through window, handheld with slight wobble no zoom no pan, 50mm slightly
shallow depth of field, warm muted palette cream and soft brown natural
skin texture, EXCLUDE income figures revenue claims dollar amounts
em dashes hyper-saturation rented luxury props

If a real client is willing to be filmed and has signed consent, swap
in real footage here. Real client > AI synthesis in the proof slot.

CTA dialogue (passed through voice gates):
- "Comment <KEYWORD> for the free framework."
- "Link in bio for the case study."
- "Tap below for the free walkthrough."
- "DM <KEYWORD> for the breakdown."

Hard rules:
- Same avatar locked across clips 1, 2, 3, 4 (or real client footage in
  clip 3 with the avatar bookending it).
- No income claims, no outcome guarantees, no refund language, no
  urgency manipulation, no rented luxury.
- Speed adjust 80-90% in CapCut for all clips (Seedance rushes).
- Caption + on-screen text must pass content-engine + humanizer voice
  gates.
- Hand final MP4 to higgsfield-ad-critic for compliance + voice review.

Compliance restatement before each clip render:
"Clip <n> render: avatar locked, no income claims, no outcome
guarantees, no urgency manipulation. Proceed? (y/n)"

Restate intent and wait for "y" before each clip.
```

**Tool params under the hood:**
- product_url: <user URL>
- campaign_goal: awareness
- avatar_mode: custom_mint_locked (or soul_id_locked)
- resolution: 1080p
- aspect: 9:16
- clip_count: 4
- formats: [ugc, tutorial, story_via_seedance_direct, cta_via_seedance_direct]
- output_dir: ~/board/_active/marketing-studio-course-<YYYY-MM-DD>/

---

## Prompt 3: CTA-Only Render (1 clip, ~150 credits, ~5 min)

Use when the full_stitch is mostly working but the CTA needs work. Coach CTAs fail most often because the urge to "make it punchier" lands you in outcome-guarantee territory.

```
Re-render only the CTA clip for the coach campaign at
~/board/_active/marketing-studio-course-<YYYY-MM-DD>/.

Avatar: same locked face from clips 1, 2, 3.
Resolution: 1080p, 9:16, 5s
Engine: Direct Seedance

CTA prompt skeleton:
5 seconds 9:16, medium close-up handheld selfie style, [avatar
description] sitting at home office desk gesturing warmly toward an
imaginary link below the frame while saying "<CTA dialogue, under 7
words>" with a warm engaged smile, soft afternoon natural light from a
window, handheld with slight wobble no zoom no pan, 50mm slightly
shallow depth of field, warm muted palette natural skin texture not
glossy, conversational warm tone voice clear not rushed,
EXCLUDE income claims outcome guarantees em dashes urgency manipulation
rented luxury props plastic AI-glossy skin

CTA copy options (pick one, must pass content-engine + humanizer gates):
- "Comment <KEYWORD> for the free framework."
- "Link in bio for the case study."
- "Tap below for the free walkthrough."
- "DM <KEYWORD> for the breakdown."
- "Link below to read the story."

CTA copy gates checklist:
- Under 7 words: y/n
- No income claim: y/n
- No outcome guarantee: y/n
- No refund language: y/n
- No urgency manipulation: y/n
- No drop-in invite: y/n
- No casual support promise: y/n
- No em dashes: y/n
- Passes content-engine: y/n
- Passes humanizer: y/n

If ANY box is "n", do not render. Rewrite, re-gate, then render.

Save as: <output>/clip-cta.mp4. Re-run the CapCut stitch and ship.
```

**Tool params under the hood:**
- engine: seedance_2.0
- avatar_lock: <slug from full_stitch run>
- duration_s: 5
- resolution: 1080p
- aspect: 9:16
- output_file: <output>/clip-cta.mp4

---

## Run order

1. Prompt 1 (cheap_test) -> hook + CTA validation + compliance check.
2. Prompt 2 (full_stitch) -> if a real client is available for clip 3, swap in real footage.
3. Prompt 3 (CTA-only) if the CTA needs a re-render or if the compliance gates flag a phrase.

**Hard rule for coach pack:** if at any point the compliance checklist fails, STOP. Rewrite the dialogue in process language, re-gate, then proceed. A rejected Meta ad costs hours; a banned account costs months.
