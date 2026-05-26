# Worked Example: Vitamin Bottle UGC Ad

Full end-to-end walk-through reproducing the Py47FzLdF9E flow with Selr AI
house-style voice. Use as a template + sanity check when building your first
UGC ad with this skill.

**Product:** "Calm Magnesium", a magnesium glycinate supplement targeted at
office workers with sleep + stress issues
**Product URL:** https://example.com/calm-magnesium (placeholder)
**Total runtime:** ~28s
**Framework:** mid-funnel punchy (5 chunks)
**Output folder:** `~/board/_active/ugc-ads-2026-05-24/`

---

## Phase 0: Confirm before building

```
Skill: I'm about to build a multi-chunk UGC ad for Calm Magnesium. Confirm:
- Product URL: https://example.com/calm-magnesium
- Total runtime target: ~28s
- Number of chunks: 5 (mid-funnel: hook / problem / solution / proof / cta)
- Character: GPT Image 2.0 generated UGC presenter (one-off, no campaign reuse)
- Voice: Megan (Higgsfield Change Voice)
- Framework: mid-funnel punchy
- Should I pull copy variants from ad-creative for CTA? Yes
- Should I run higgsfield-ad-critic on the final cut? Yes

User: confirmed.
```

Skill writes `06-brief.md` with all of the above.

---

## Phase 1: Product still

User has a messy product photo (capsules visible outside bottle, mixed
background). Skill invokes `selrai-ad-image` with this prompt:

```
Generate a high quality render of this product image against a clean
off-white background. Remove the loose capsules outside the bottle. Keep
the bottle label crisp and centered. Add a soft natural shadow under the
bottle for realism. No studio glare, no rim light, no e-commerce hero look.
```

Output saved to `~/board/_active/ugc-ads-2026-05-24/00-product-still.png`.

Uploaded to Higgsfield → Elements → tagged as `@product`.

---

## Phase 2: Character lock

Path C, one-off generated UGC presenter via GPT Image 2.0:

```
Generate a candid and natural photo of a woman in her early 40s standing in
her modern apartment kitchen. Soft natural light from a window at her right.
Shoulder-length brown hair, loosely tied back, slightly messy. Wearing a
heather grey cotton t-shirt. No makeup, lightly tanned, soft features.
Selfie-style framing, slight wobble, imperfect eye-level. 9:16 vertical, 2K.
```

Output saved to `~/board/_active/ugc-ads-2026-05-24/01-character-ref.png`.

Reference image will be re-attached per chunk in Phase 5.

---

## Phase 3: Hook brainstorm (Chat 1)

Chat 1 opened. User pastes the handoff message from
`prompts/01-hook-brainstorm.md`.

Chat 1 asks back:

1. Tone? → founder voice ("I tried this") not influencer voice
2. Current ad? → none, this is the first
3. Ruled-out angles? → no fear-of-missing-out, no comparison to competitor brands
4. ICP? → office workers, 30–50, struggling with sleep + stress
5. Name product in hook? → no, hold for Chunk 3 reveal (higher curiosity)
6. Unique mechanism? → 400mg magnesium glycinate per capsule (most brands use cheaper magnesium oxide)

User answers. Chat 1 returns:

```
HOOK VARIATIONS

1. [archetype: PAIN]
   "I haven't slept more than 5 hours in 8 months."

2. [archetype: CURIOSITY]
   "There's one mineral most office workers are missing."

3. [archetype: CONTRARIAN]
   "Melatonin made my sleep worse, not better."

4. [archetype: PROOF / NUMBERS]
   "Two weeks ago my Oura ring score went from 62 to 84."

5. [archetype: AUTHORITY]
   "My GP told me I was magnesium deficient before I even asked."

REJECTED (considered but cut)
- "This sleep hack changed my life", banned vocab (changed my life)
- "What if I told you the secret to sleep is one supplement?", too on-the-nose, "secret"
- "Office workers, listen up", too generic
```

User picks #3 (CONTRARIAN). It pattern-interrupts (most sleep ads push
melatonin) and stands alone. Hook locked.

---

## Phase 4: Multi-chunk script (Chat 2)

Chat 2 opened (fresh context). User pastes the handoff from
`prompts/02-multi-chunk-script.md` with:

- Product: Calm Magnesium, magnesium glycinate supplement for sleep + stress
- URL: https://example.com/calm-magnesium
- Character path: GPT Image (one-off), reference at 01-character-ref.png
- Voice: Megan
- Framework: mid-funnel punchy
- Chosen hook: [CONTRARIAN], "Melatonin made my sleep worse, not better."
- Total runtime: ~28s
- Chunks: 5
- ICP: office workers, 30–50, sleep + stress
- Mechanism: 400mg magnesium glycinate per capsule (vs cheap magnesium
  oxide most brands use)
- CTA action: visit the product URL

Chat 2 emits `02-script.yaml`:

```yaml
campaign_name: "Calm Magnesium, mid-funnel-punchy, 2026-05-24"
character_lock:
  age: "early 40s"
  gender: "woman"
  appearance: >
    A candid, natural woman in her early 40s, lightly tanned, soft features,
    no makeup, shoulder-length brown hair loosely tied back, wearing a
    heather grey cotton t-shirt. Energy is grounded and slightly tired, not
    influencer-perky.
  voice: "Megan"
  soul_id: null
  reference_image_path: "~/board/_active/ugc-ads-2026-05-24/01-character-ref.png"
universal_directions:
  hair: >
    Shoulder-length brown, loosely tied back, slightly messy, no salon
    styling, flyaways visible. Identical in every chunk.
  application: >
    Holds bottle in left hand at chest height. Never centered to camera.
    Occasionally glances at the label but mostly looks at the lens. Uncaps
    with right hand thumb, taps one capsule into right palm, does not show
    capsule contents.
  b_roll: >
    Modern apartment kitchen. Soft natural light through a tall window at
    camera-right. Wood countertop, ceramic mug to the left, succulent plant
    visible just out of focus behind her. Same setup across every chunk.
  ugc_realism_notes: >
    Selfie handheld, slight wobble, imperfect framing, candid, no studio
    look, micro-pauses in delivery, occasional glance away from lens before
    returning. Skin texture visible, no smoothing.
chunks:
  - id: 1
    role: hook
    voiceover: "Melatonin made my sleep worse, not better."
    runtime: 4
    product_tag: null
    framing: "selfie handheld, eye-level, shoulders and face fill frame, kitchen background slightly blurred"
    include_product: false
  - id: 2
    role: problem
    voiceover: "I'd wake up at 3am, foggy all day, then crash by 8pm. Two months of that."
    runtime: 6
    product_tag: null
    framing: "selfie handheld, slightly lower angle, looks off-camera at a coffee mug, brows lightly furrowed"
    include_product: false
  - id: 3
    role: solution
    voiceover: "My GP said I was magnesium deficient. So I tried Calm Magnesium."
    runtime: 6
    product_tag: "@product"
    framing: "selfie handheld, character reaches off-screen right and brings bottle into frame at chest height, holds at slight angle"
    include_product: true
  - id: 4
    role: proof
    voiceover: "It's 400mg of magnesium glycinate, not the cheap oxide. Three weeks in and I sleep through the night."
    runtime: 8
    product_tag: "@product"
    framing: "medium shot, character uncaps bottle with right thumb, taps one capsule into left palm, looks at lens then at capsule"
    include_product: true
  - id: 5
    role: cta
    voiceover: "Link in bio if you want to try it. Use code SLEEP for 20 off."
    runtime: 4
    product_tag: "@product"
    framing: "selfie handheld, product held up at chest height, direct eye contact with lens, soft smile"
    include_product: true
final_cta:
  voiceover: "Link in bio if you want to try it. Use code SLEEP for 20 off."
  runtime: 4
  on_screen_url: "example.com/calm-magnesium"
_meta:
  skill_version: "1.0.0"
  created: "2026-05-24"
  updated: "2026-05-24"
  framework: "mid-funnel-punchy"
  chosen_hook_archetype: "CONTRARIAN"
  total_regenerate_iterations: 0
  critic_verdict: "PENDING"
  ship_gate:
    content_engine: "PENDING"
    humanizer: "PENDING"
```

Style audit passes, no em dashes, no banned vocab. Outcome language is
observed-result ("I sleep through the night"), not guarantee ("you'll sleep
through the night").

Chat 2 also writes the 5 per-chunk render blocks to
`chunks/chunk-{1..5}-prompt.md` using `templates/chunk-prompt-template.md`.

Aggregator `02-script-pasteable.md` written for one-paste workflows.

---

## Phase 5: Render each chunk

Higgsfield Seedance 2.0 opened. `@product` tag confirmed in Elements panel.
Reference image `01-character-ref.png` ready to attach.

**Chunk 1 (hook, 4s, no product):**
- `@product` REMOVED from Elements panel.
- Reference image attached.
- Paste `chunk-1-prompt.md`.
- Aspect 9:16, 720p, 4s.
- Generate.
- Returns in 28s. Looks good. Voice is "Default Female 2". Note for Chunk 2.
- Download to `chunks/chunk-1.mp4`.

**Chunk 2 (problem, 6s, no product):**
- `@product` REMOVED from Elements panel.
- Reference image attached.
- Paste `chunk-2-prompt.md`.
- Generate.
- Returns in 32s. Looks good. Voice is "Default Female 3", different from
  Chunk 1.
- Click **Change Voice** → pick "Megan" (matches Chunk 1).
- Download to `chunks/chunk-2.mp4`.

**Chunk 3 (solution, 6s, product visible):**
- `@product` ADDED to Elements panel.
- Reference image attached.
- Paste `chunk-3-prompt.md`.
- Generate.
- Returns in 38s. Product looks right (label readable, bottle shape matches).
  But hair is slightly different from Chunks 1 + 2 (more wave).
- Apply Change Voice → Megan.
- Decision: hair drift is minor enough to leave (would cost 4 credits to
  regenerate). Note for critic in Phase 7.
- Download to `chunks/chunk-3.mp4`.

**Chunk 4 (proof, 8s, product visible + active use):**
- `@product` stays loaded.
- Reference image attached.
- Paste `chunk-4-prompt.md`.
- Generate.
- Returns INSTANT-FAIL in 6s. Content filter rejection.
- Diagnosis: voiceover line mentions "magnesium glycinate, not the cheap
  oxide", "cheap" can trigger comparative-advertising filter.
- Rewrite to: "It's 400mg of magnesium glycinate, the form your body
  actually absorbs. Three weeks in and I sleep through the night."
- Re-paste. Generate.
- Returns in 41s. Looks great. Capsule visible briefly in palm, minor AI
  artifact (capsule shape morphs at frame 6/8s). Decision: cover in CapCut
  with B-roll overlay from Chunk 3.
- Apply Change Voice → Megan.
- Download to `chunks/chunk-4.mp4`.

**Chunk 5 (cta, 4s, product held up):**
- `@product` stays loaded.
- Reference image attached.
- Paste `chunk-5-prompt.md`.
- Generate.
- Returns in 24s. Looks great. Direct eye contact lands. Smile reads soft,
  not infomercial.
- Apply Change Voice → Megan.
- Download to `chunks/chunk-5.mp4`.

**Credit spend so far:** ~28 credits (5 chunks × ~5 average, plus 1 filter
fail × 0 charge, plus 1 regenerate on chunk 4). Well under the 1.5× budget.

---

## Phase 6: CapCut assembly

Per `../shared/capcut-finishing.md`:

1. Import chunks 1–5 in order.
2. Tighten cuts: 0.1s gap between each.
3. Speed adjustment: none (delivery is natural across all chunks).
4. B-roll overlay: at 4.5s into Chunk 4 (where the capsule morphs), overlay
   a 0.5s snippet from Chunk 3 (the bottle reach) + mute that section's
   audio.
5. Auto-captions: enable, Classic preset, black outline, position raised.
6. Music: none (UGC test, voice-only often performs better on cold).
7. Export: 1080p, 30fps, H.264, MP4.

Final cut saved to `~/board/_active/ugc-ads-2026-05-24/03-final-1080p.mp4`.

---

## Phase 7: Critique loop (Chat 3)

Chat 3 opened. User pastes the handoff from
`prompts/04-critique-and-revise.md` with the path to `03-final-1080p.mp4`.

`higgsfield-ad-critic` (Gemini-backed) returns `04-critique-v1.md`:

```
CRITIQUE REPORT, ugc-ad-2026-05-24, v1

SCORE
- Hook strength: 8/10, "Melatonin made my sleep worse, not better." is
  contrarian + sayable + stops scroll on a saturated category. Solid.
- Product visibility timing: PASS, first reveal at 10.2s (mid Chunk 3),
  appropriate for mid-funnel.
- Character consistency: PASS with caveat, slight hair wave change on
  Chunk 3, recovered on Chunks 4-5. Below regenerate threshold.
- Voice consistency: PASS, Megan applied across all chunks via Change
  Voice. Consistent.
- Pacing: PASS, no chunk feels rushed or dragging. Chunk 4 at 8s is the
  longest, which is appropriate for proof.
- AI-look tells: 1 spotted, micro-flicker at 14.7s where the capsule
  appears in palm. Covered by B-roll overlay in CapCut. Good catch.
- CTA clarity: 7/10, "Link in bio if you want to try it" is clear, but
  "Use code SLEEP for 20 off" should specify currency or % (is it $20 or
  20%?). Recommend changing to "20% off".
- Voice ban-list compliance: PASS, no em dashes, no banned vocab, no
  outcome guarantees.

ISSUES (sorted by severity)

1. [Severity: MED] [Chunk 5]
   What: CTA ambiguity, "20 off" not clear if dollar or percent.
   Why it matters: Ambiguous discount kills conversions on cold traffic.
   Fix: CapCut fix (overlay text) OR Single-chunk regenerate.
   Specific instruction: Add on-screen overlay "20% OFF, CODE: SLEEP" at
   the 26s mark for 4s. Match brand purple. OR regenerate Chunk 5 with
   voiceover "Use code SLEEP for 20% off".

GREEN-LIGHT or NOT-YET
- GREEN-LIGHT (after applying the MED fix on Chunk 5)
```

User applies the CapCut overlay fix (cheaper than regenerating the chunk).
Re-export `03-final-1080p.mp4`.

Re-loop. Critic returns `04-critique-v2.md`:

```
GREEN-LIGHT, no remaining issues.
```

---

## Phase 8: Ship gate

Final caption + on-screen text + hashtags drafted:

```
Caption:
Was 3am wake-ups for 2 months. GP said magnesium deficient. Calm Magnesium
fixed it in 3 weeks. Code SLEEP at the link.

#sleep #magnesium #wellness #ugc
```

Run through `content-engine` → PASS. No em dashes, no banned vocab.

Run through `humanizer` → minor suggestion: "Calm Magnesium fixed it" reads
as outcome-claim. Rewrite to "Calm Magnesium worked for me in 3 weeks." →
re-run → PASS.

Final caption:

```
Was 3am wake-ups for 2 months. GP said magnesium deficient. Calm Magnesium
worked for me in 3 weeks. Code SLEEP at the link.

#sleep #magnesium #wellness #ugc
```

Both gates PASS. Skill writes `05-ship-checklist.md` with timestamp + final
caption + critic green-light + gate results.

Ad is shipped. Total time: ~75 minutes. Total credit spend: ~28. Total
ad-creative-cost: $0 outside the Plus plan subscription.

---

## Reflection, what would have gone wrong without this skill

1. Without the multi-chunk YAML, the hair drift on Chunk 3 would have
   cascaded, by Chunk 5, the character would have read as a different
   person. The universal direction block fixes this.
2. Without the `@product` tag, the bottle would have hallucinated a
   different shape on every chunk. The Elements panel discipline fixes this.
3. Without the two-chat split, the production chat (Chat 2) would have run
   out of context by Chunk 4. The hook brainstorm alone would have burned
   8K tokens.
4. Without the critic loop, the CTA ambiguity ("20 off") would have shipped.
5. Without the content-engine + humanizer ship-gate, "Calm Magnesium fixed
   it" would have shipped as an outcome-claim and triggered Selr AI's
   own "no outcome guarantees" rule (and likely IG ad-policy review).

The skill exists to prevent all five of these by default.
