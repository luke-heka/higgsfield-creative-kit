# Prompt 05. Assemble + Ship

Step 5 of the Marketing Studio orchestration. Goal: stitch the rendered
clips into the final 35-60s spot, voice-grade every text artifact, run
the critic, and produce a ship-ready bundle.

---

## Pre-flight gate

Before assembly:

- [ ] All clips in `01-format-list.md` exist as MP4 files in `<output>/`.
- [ ] `clip-cta.mp4` exists.
- [ ] Each clip passed its per-clip human gate (or has a B-roll cover
      plan noted in `cost-log.md`).
- [ ] CapCut is installed and open.

---

## Assembly in CapCut

Follow `../../shared/capcut-finishing.md` for the full recipe. Skill-specific
deltas below.

### 1. Import in order

Drag onto the timeline in the order from `01-format-list.md`:

```
clip-1-ugc.mp4 → clip-2-tutorial.mp4 → clip-3-unboxing.mp4 → clip-4-review.mp4 → clip-cta.mp4
```

For awareness or retention mixes, your order differs, follow your
format list, not this example.

### 2. Speed adjust

Per clip, right-click → Speed → Normal → **80-90%**.

Why: Marketing Studio's Seedance 2.0 backbone tends to rush voiceover
delivery. 80-90% reads more natural. Below 80% the pitch drops audibly.

### 3. B-roll overlay for hallucination repair

For any clip flagged in the per-clip human gate (face morph, hand glitch,
product warp):

- Drop the unboxing clip OR a still frame from a clean clip on the
  overlay track.
- Position over the bad frame(s).
- Mute the underlying clip's audio for that section.
- Audio from the next clip carries through.

See `../../shared/capcut-finishing.md` Fix 2 for the detailed pattern.

### 4. Audio sync + mute

- Listen end-to-end with headphones.
- Mute any clip where the VO is unsalvageable (garbled, rushed past
  fixing). Cover with the next clip's audio or a clean voiceover layer.
- For multi-language ads: use CapCut's Change Voice button to maintain
  voice consistency across clips without burning new Higgsfield credits.

### 5. Auto-captions

- Click Auto-Captions → English (or campaign language).
- Style: **Classic preset**.
- Color: brand color (e.g. yellow on dark, white on light).
- Position: raised 15-20% from the bottom (avoids platform UI overlap).

### 6. Export

- Resolution: 1080p (or 720p for cheap_test).
- Format: H.264 MP4.
- Aspect: 9:16.
- Output filename: `<output>/final-ad.mp4`.

---

## Voice-grade every text artifact (HARD GATE)

Before ship, every text artifact passes through both gates:

### Artifacts to gate

- **On-screen text in CapCut** (any title cards, overlays, end frames)
- **Auto-caption corrections** (CapCut transcribes the VO; review and
  correct any typos)
- **Social caption** (the post copy that ships with the ad)
- **CTA copy** (the "Click the link below to shop now" or campaign equiv)

### The gates

1. `content-engine`, verified Luke voice filter. Output must read as
   Luke / Selr AI, not generic AI prose.
2. `humanizer`, 21-category AI writing pattern scrubber + slop blocklist.

### Banned vocab (auto-fail)

- game-changer
- 10x
- crushing it
- killing it
- secret sauce
- level up
- unlock
- transform

### Banned punctuation

- Em dashes, replace with commas or full stops.

### Banned phrasings

- Outcome guarantees ("this ad will get you 10x ROAS")
- Refund / money-back promises
- Casual drop-in invites ("come say hi", "swing past")
- Personal life references (founder's family, kids, partner)

### If a draft fails

- Rewrite. Re-run both gates. Ship only when both pass.
- Never ship "close enough", voice failures cost more than a regen.

---

## Write the final caption + CTA

Save to `<output>/caption.md`:

```markdown
# Final Caption + CTA

## Social caption (for Meta / TikTok / Reels post)

<voice-graded caption, 80-150 words max, no em dashes>

## CTA copy (used in CTA clip + link sticker)

<voice-graded CTA, 1 line, action verb, no outcome promise>

## Hashtags (if applicable)

<5-10 hashtags relevant to product + audience>
```

---

## Hand to higgsfield-ad-critic

If `higgsfield-ad-critic` skill exists:

- Pass `<output>/final-ad.mp4` to the critic.
- Critic returns a structured report on: hook strength, pacing,
  hallucination check, CTA legibility, caption-VO sync, overall ship
  readiness.
- Save the report to `<output>/critic-report.md`.
- If critic returns FAIL: address the named issues. Re-export the
  CapCut project. Re-run critic.
- If critic returns PASS WITH NOTES: address what's reasonable, ship
  with the notes logged.

If `higgsfield-ad-critic` does not exist yet:

- Skip the critic step.
- Write a placeholder `<output>/critic-report.md` with: "TODO, run
  higgsfield-ad-critic when skill becomes available."

---

## Final cost log

Update `<output>/cost-log.md` with the totals row:

```markdown
| Stage | Credits | USD (Plus plan, $0.012/credit) |
|-------|---------|--------------------------------|
| Avatar mint (Tier 1) | 50 | $0.60 |
| Clip renders (5 clips, 1080p) | 875 | $10.50 |
| Regens | <n> | <$x> |
| **TOTAL** | <n> | <$x> |

**Time spent (human):**
- Intake + product ingest: ~10 min
- Format selection: ~5 min
- Avatar mint: ~5 min
- Render loop with gates: ~30-45 min
- CapCut assembly: ~20 min
- Voice gates + critic: ~15 min
- **Total: ~90-100 min**

**Comparison:** traditional UGC agency for equivalent ad ≈ $500-1,500
USD + 2-week turnaround. Freelance ≈ $200-400 USD + 1 week.
```

---

## Update board + log

- Append to `~/board/_log.md`:

```markdown
- YYYY-MM-DD, Marketing Studio campaign shipped: <product name>, <goal>, $<x>, ~<n>min
```

- If this campaign is part of an active project in `~/board/_active/`,
  update that project file (move task to Done, update `updated` date).

- If this is a one-off, the output folder IS the artifact, no further
  board update needed.

---

## Ship handoff

The final folder:

```
~/board/_active/marketing-studio-<YYYY-MM-DD>/
├── 00-product-card.png
├── 00-brief.md
├── 01-format-list.md
├── clip-1-ugc.mp4
├── clip-2-tutorial.mp4
├── clip-3-unboxing.mp4
├── clip-4-review.mp4
├── clip-cta.mp4
├── final-ad.mp4         ← upload this
├── caption.md           ← paste this
├── critic-report.md
└── cost-log.md
```

Hand the user this folder path. They upload `final-ad.mp4` to their ad
platform (Meta Ads, TikTok Ads Manager, Reels organic, YouTube Shorts)
and paste `caption.md` content into the post copy field.

For Meta Ads upload, route to the `meta-ads` skill (do NOT auto-upload
, that's a separate human gate).

---

## Output

Final ship bundle in `<output>/`. Skill run complete.
