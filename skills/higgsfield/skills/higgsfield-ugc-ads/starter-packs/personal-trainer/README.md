# Personal Trainer Starter Pack

**Built for:** personal trainers, fitness coaches, gym owners, and online coaches selling 1:1, online coaching, or small-group training in Australia. Tested against the 2026 PT/fitness patterns in the starter-pack industry research.

**What this pack ships:**
- `brief.md`, a preconfigured 5-chunk mid-funnel-punchy multi-chunk-script intake with the gym-floor PT avatar and Australian commercial gym aesthetic pre-locked
- `prompts.md`, 3 paste-ready Seedance 2.0 chunk prompts (hook, solution, CTA)
- This README

**Time:** 60 to 90 minutes from trainer headshot to finished MP4 on a clean run.

**Credits:** ~28 credits per ad on Plus plan ($49/mo), budget 1.5× = ~42 credits for fail-buffer.

---

## 60-second how-to

### Step 1, edit 5 to 11 fields in `brief.md`

Open `brief.md` and replace every `{{VARIABLE}}` with the trainer's value. The 5 fields you MUST edit:

1. `{{BUSINESS_NAME}}`, your studio or brand
2. `{{TRAINER_NAME}}`, the trainer on camera
3. `{{OFFER}}`, what you're selling + price anchor
4. `{{LOCATION}}`, suburb + state for local SEO
5. `{{BOOKING_URL}}`, DM keyword OR booking page

Optional polish:
6. `{{CLIENT_AVATAR}}`, who the ad is for
7. `{{COMMON_MISTAKE}}`, the form / habit you fix
8. `{{SIGNATURE_METHOD}}`, your named method
9. `{{TIMEFRAME}}`, how long until clients notice change
10. `{{HERO_BENEFIT}}`, the outcome in the client's words
11. `{{TRAINER_TAG}}`, character Element tag (default `@trainer`)

### Step 2, pre-mint the trainer reference image

Use GPT Image 2.0 (UGC characters render best on it) with: *"Generate a candid and natural photo of an athletic personal trainer in her early 30s standing in a real Australian gym, branded training singlet, hair tied back, direct warm expression."*

Save to `~/board/_active/ugc-ads-<YYYY-MM-DD>/01-character-ref.png`. Upload to Higgsfield → Elements → tag as `@trainer`.

If you're using a real trainer (not a generated avatar), upload a real headshot to Elements instead. For a trainer doing 4+ ads, mint a Soul ID via `higgsfield-soul` so the face never drifts across campaigns.

### Step 3, invoke the parent skill

```
/skill higgsfield-ugc-ads
```

Paste the contents of `brief.md` when prompted. The skill will load the character_lock + universal_directions + 5 chunks, run Phase 1 to 8, produce a finished 1080p MP4.

### Step 4, render the 5 chunks

For each chunk, paste the matching block from `prompts.md` (chunk 1, 3, 5 are pre-written; chunks 2 and 4 are derived by the parent skill). The `@trainer` Element tag stays loaded across all 5 chunks. Do not toggle.

### Step 5, assemble in CapCut

Follow `../shared/capcut-finishing.md`. Auto-captions on (mandatory for fitness, most watched on mute). Tight cuts between chunks. Export 1080p H.264 MP4.

### Step 6, ship-gate

Run the final caption + on-screen text through `content-engine` and `humanizer`. Both must PASS before posting.

---

## What this pack will NOT do for you

- Won't write specific weight-loss numbers ("lose 10kg in 8 weeks"). Meta auto-rejects these.
- Won't write body-shame language ("stop being lazy", "this is why you're not losing weight"). Kills DM conversion and gets reported.
- Won't generate shirtless-flex aesthetics. Female client conversion (70% of online coaching) drops sharply when the trainer ad reads as "fitness model" instead of "coach".
- Won't fake before/afters. If you swap in a transformation reel, the client must have signed consent and the timeframe must be true.
- Won't generate the IG caption. That's `ad-creative`'s job, invoke it after rendering.

---

## When to swap to a different pack

| If your business is... | Use this instead |
|------------------------|------------------|
| A DTC product (supps, skincare, apparel) | `../dtc-ecommerce/` |
| A plumber, sparky, cafe, salon, restaurant | `../local-service-trade/` |
| A high-ticket course or coach (not fitness) | use the parent skill's default flow (no starter pack covers this yet) |

---

## Compliance summary (read before editing copy)

- **No specific weight-loss numbers.** Use feeling-based outcomes ("walking up stairs feels easier", "strength building").
- **No body shaming.** No "you're lazy", no "stop making excuses", no "before" framing that calls out current body shape.
- **No outcome guarantees.** "Guaranteed transformation", "results or refund", "money-back", banned.
- **No banned vocab** ("transform", "level up", "crushing it", "killing it", "10x"), the ship-gate hard-fails.
- **AU English default.** Use organised, optimise, colour. Voiceover phrasing is Australian-conversational.
- **Real client proof only.** If you name a client in the proof line (chunk 4), get signed consent.

---

## Credit estimate

| Item | Credits |
|------|---------|
| 5 chunks × ~5 credits each on 720p Plus plan | 25 |
| 1.5× regenerate buffer (Seedance ~30% first-pass fail) | +13 |
| Trainer reference on GPT Image 2.0 (Phase 2) | 0 on Ultra, 5 on Plus |
| Soul ID mint (one-time, recommended for repeat campaigns) | ~10 on Plus, 0 on Ultra |
| **Total budget** | **~28 to 42 credits per ad** |

For a trainer running 8 ads a month, mint Soul ID once, then average ~30 credits per ad after that. Plus plan ($49/mo) covers ~24 ads at this budget. Ultra plan ($99/mo) covers ~75.
