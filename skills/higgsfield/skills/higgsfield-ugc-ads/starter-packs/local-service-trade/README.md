# Local Service Trade Starter Pack

**Built for:** local trade and hospo businesses, plumbers, electricians, cafes, hairdressers, restaurants, in Australia. Tested against the 2026 local-trade/hospo patterns in the starter-pack industry research (TikTok Local Feed launched Feb 2026, location-based discovery is the dominant lead-gen channel).

**What this pack ships:**
- `brief.md`, a preconfigured 5-chunk mid-funnel-punchy multi-chunk-script intake with the owner-on-site avatar and Australian worksite/kitchen aesthetic pre-locked
- `prompts.md`, 3 paste-ready Seedance 2.0 chunk prompts (hook, solution, CTA)
- This README

**Time:** 60 to 90 minutes from owner photo to finished MP4 on a clean run.

**Credits:** ~28 credits per ad on Plus plan ($49/mo), budget 1.5× = ~42 credits for fail-buffer.

---

## 60-second how-to

### Step 1, edit 5 to 11 fields in `brief.md`

Open `brief.md` and replace every `{{VARIABLE}}` with the business's value. The 5 fields you MUST edit:

1. `{{BUSINESS_NAME}}`, the business
2. `{{OWNER_NAME}}`, the owner on camera
3. `{{TRADE_TYPE}}`, the category (plumbing, cafe, salon, etc.)
4. `{{LOCATION}}`, suburb + state for local SEO
5. `{{BOOKING_URL_OR_KEYWORD}}`, DM keyword OR booking page

Optional polish:
6. `{{SERVICE_AREA}}`, the areas you cover (trades) or opening hours (hospo)
7. `{{SIGNATURE_OFFERING}}`, the dish, the job, the cut that defines you
8. `{{PRICE_ANCHOR}}`, specific price, no vague ranges
9. `{{USP}}`, the one reason a buyer picks you
10. `{{OWNER_TAG}}`, character Element tag (default `@owner`)
11. `{{ASSET_TAG}}`, workspace tag (`@truck`, `@kitchen`, `@chair`)

### Step 2, pre-mint TWO reference images

This pack uses two Element tags:

**Owner reference:** GPT Image 2.0 with: *"Generate a candid and natural photo of a {{TRADE_TYPE}} business owner in his late 30s standing on-site in a real Australian {{TRADE_TYPE}} setting, branded shirt, direct warm expression."* Save to `~/board/_active/ugc-ads-<YYYY-MM-DD>/01-character-ref.png`. Upload to Higgsfield → Elements → tag as `@owner`.

**Asset reference:** Nano Banana 2 with: *"Generate a high-quality render of a [branded Hilux ute with signwriting / cafe counter with branded apron / salon chair with mirror behind] in a real on-site setting, no people in frame, natural light."* Save to `00-asset-still.png`. Upload to Higgsfield → Elements → tag as your `{{ASSET_TAG}}` (`@truck`, `@kitchen`, `@chair`).

For hospo, the asset tag is optional. The owner holding the dish is often enough.

### Step 3, invoke the parent skill

```
/skill higgsfield-ugc-ads
```

Paste the contents of `brief.md` when prompted. The skill loads the character_lock + universal_directions + 5 chunks, runs Phase 1 to 8, produces a finished 1080p MP4.

### Step 4, render the 5 chunks (with the two-tag toggle)

For each chunk, paste the matching block from `prompts.md` (chunk 1, 3, 5 are pre-written; chunks 2 and 4 are derived by the parent skill).

**Tag toggle is critical here:**
- Chunks 1, 2: `@owner` LOADED, `{{ASSET_TAG}}` REMOVED
- Chunks 3, 4, 5: BOTH `@owner` AND `{{ASSET_TAG}}` LOADED

Get the toggle wrong and the workspace either appears in the hook (kills the punch) or disappears from the CTA (loses the brand cue).

### Step 5, assemble in CapCut

Follow `../shared/capcut-finishing.md`. Auto-captions mandatory. **Use the blur tool** to mask any plate numbers, street numbers, or customer faces that snuck into the render. Export 1080p H.264 MP4.

### Step 6, ship-gate

Run the final caption + on-screen text through `content-engine` and `humanizer`. Both must PASS before posting.

---

## What this pack will NOT do for you

- Won't write false response-time promises ("we'll be there in 30 minutes", "guaranteed same-day"). ACL audits these for trades.
- Won't generate "we're the best in [city]" flat claims without proof. The hook frames it as a question, not a claim.
- Won't film inside a customer's property. The owner-on-site avatar lives in YOUR ute, YOUR kitchen, YOUR salon, never the customer's.
- Won't write a phone-only CTA. Meta and TikTok both demote phone-only CTAs in 2026.
- Won't generate the IG caption. That's `ad-creative`'s job, invoke it after rendering.

---

## When to swap to a different pack

| If your business is... | Use this instead |
|------------------------|------------------|
| A DTC product (supps, skincare, apparel) | `../dtc-ecommerce/` |
| A personal trainer or fitness coach | `../personal-trainer/` |
| A real estate agent, coach, course, SaaS | use the parent skill's default flow (no starter pack covers this yet) |

---

## Compliance summary (read before editing copy)

- **No false response-time promises.** "We'll be there in 30 minutes", "guaranteed same-day", banned unless you actually deliver consistently and can prove it.
- **No customer property in frame.** Plate numbers, street numbers, customer faces, all masked. Use the CapCut blur tool.
- **No "we're the best in [city]" without proof.** The hook frames it as a question.
- **No phone-only CTA.** DM keyword OR online booking URL. Phone is a secondary mention only.
- **CASA drone rules.** No drone over private property without written consent (trades). Your own shopfront is fine.
- **No banned vocab** ("game-changer", "10x", "unlock", "transform", "revolutionary"), the ship-gate hard-fails.
- **AU English default.** Mate, ute, mob, sorted, organise, colour, optimise.

---

## Credit estimate

| Item | Credits |
|------|---------|
| 5 chunks × ~5 credits each on 720p Plus plan | 25 |
| 1.5× regenerate buffer (Seedance ~30% first-pass fail) | +13 |
| Owner reference on GPT Image 2.0 (Phase 2) | 0 on Ultra, 5 on Plus |
| Asset reference on Nano Banana 2 (Phase 1) | 0 on Ultra, 3 on Plus |
| **Total budget** | **~28 to 42 credits per ad** |

For a trade or hospo business running 4 ads a month, Plus plan ($49/mo) covers ~24 ads at this budget. Ultra plan ($99/mo) covers ~75. If you're running ads weekly for a single location, Plus is enough.

---

## Trade-specific notes

**Plumbing / electrical / restoration:** the "satisfying-job-reveal" hook works best (chunk 1 can show the messy before, chunk 4 shows the clean after). Swap the hook in `brief.md` to: *"This is what was actually behind the wall."* Then pre-render two asset stills, the before-mess and the after-clean.

**Cafe / restaurant:** the "sensory hospo hook" works best (1 second cheese-pull or latte-art pour with no words, voiceover at 3s). Swap chunk 1's voiceover to a 3-second beat then the line at the 3s mark. Pre-render the signature dish as the asset tag.

**Hairdresser / salon:** the "behind-the-counter reveal" works best. Pre-render the salon chair + mirror as the asset tag. Chunk 4 demonstrates the cut in action (real client face masked or shot from behind only).

**Restaurant (sit-down):** swap the `{{SIGNATURE_OFFERING}}` to a hero dish + price anchor combo ("the $34 pork belly with apple slaw"). TikTok Local Feed weights specific dish names with price 4x over generic "dinner".
