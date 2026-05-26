---
name: higgsfield-marketing-studio
description: >
  Use when the user wants to use Higgsfield Marketing Studio, run a one-prompt
  campaign from a product URL, generate a no-prompt UGC ad, build a multi-format
  stitched ad (UGC hook + Tutorial + Unboxing + Product Review + CTA), produce
  the lowest-skill-barrier path from product link to 45-60s ad spot, or scale
  AI UGC for ecom/dropshipping where the landing page becomes the creative brief.
  This is the URL-driven path (Marketing Studio scrapes the product landing
  copy and generates with zero text prompt). For the script-driven multi-chunk
  UGC path see `higgsfield-ugc-ads`. For the brand-brief CMO-style multi-channel
  campaign see `higgsfield-cmo-agent`.
user-invocable: true
metadata:
  tags: [higgsfield, marketing-studio, ugc, no-prompt, ecom, stitch, multi-format, campaign, ad-production]
  version: 1.0.0
  updated: 2026-05-24
  parent: higgsfield
---

# Higgsfield Marketing Studio (One-Prompt-to-Campaign Orchestrator)

## What this is, in plain English

**One-liner:** Paste a product URL and pick a campaign goal; the skill scrapes your landing page, picks an avatar, and renders a 45-60 second multi-format ad (UGC + tutorial + unboxing + review + CTA) with no prompt-writing required.

**Use it when you want to:**
- Have a finished ad ready in under an hour without writing a single prompt
- Test ad creative for a new product before you spend money on real filming
- Stitch one longer ad out of 5 different angles (hook, demo, proof, review, action)
- Spin up paid-ad creative straight from an ecom product page

**Don't use it for:**
- Script-driven multi-chunk UGC where you've already written the dialogue (use `higgsfield-ugc-ads`)
- A full multi-channel marketing campaign covering paid + email + social + DM (use `higgsfield-cmo-agent`)

**Roughly:**
- ~900 credits per finished 45-60s stitched ad (any plan, Marketing Studio = Seedance 2.0 backbone). On Plus ($39/mo annual, 1,000 credits/mo) that's one stitch per month. On Ultra ($99/mo annual, 3,000 credits/mo + 8/8 parallel + UNLIMITED Nano Banana Pro for avatar mints) you can run three full stitches per month and custom-mint as many avatars as you want.
- Cheap_test mode (2 clips: UGC hook + CTA only) is ~200 credits and is mandatory before committing to a full stitch.
- Around 30-60 minutes from product URL to finished MP4.
- You get: stitched 1080p 9:16 MP4 + voice-graded caption + cost log.

**Inputs you'll need:**
- A product URL with real landing-page copy (not just a name and price)
- Campaign goal: awareness, conversion, or retention
- Optional: a custom avatar look (recommended over the default library)

---

## What This Skill Does

Takes a single **product URL** plus a **campaign goal** and orchestrates the
full Marketing Studio multi-format stitch all the way to a finished 45-60s
ad spot:

```
product URL + goal
  → Marketing Studio ingest (scrapes landing copy, builds brief silently)
  → format selection (pick from UGC / Tutorial / Unboxing / Product Review / CTA)
  → avatar decision (default vs custom mint vs Soul ID)
  → 5-clip render sequence (Seedance 2.0 backbone, character consistency)
  → CapCut assembly (stitch + captions + audio sync)
  → content-engine voice gate (mandatory on any caption / on-screen text)
  → humanizer slop gate (mandatory)
  → higgsfield-ad-critic review (post-render critique)
  → ad spot ready to upload
```

Marketing Studio is Higgsfield's **no-prompt** feature, the landing page IS
the brief. You never write a creative prompt. The skill's job is to
sequence the right format combinations, hold avatar consistency across
clips, and stitch them into a real ad (15s is not enough to convert, the
power is in the multi-format compound).

**Lowest-skill-barrier entry to full ad production** in the Higgsfield
stack. If the user is new to AI ads and wants results today, start here
before recommending `higgsfield-ugc-ads` (which needs a written script).

---

## When To Use This Skill (vs Sibling Skills)

| User says | Right skill |
|-----------|-------------|
| "Use Higgsfield Marketing Studio" | **This skill** |
| "Make me an ad from this product URL" | **This skill** |
| "One-prompt ad from a Shopify page" | **This skill** |
| "Stitch a multi-format ad" | **This skill** |
| "No-prompt UGC for my store" | **This skill** |
| "Write me a UGC ad script then render it" | `higgsfield-ugc-ads` |
| "Multi-chunk UGC with a custom Soul character" | `higgsfield-ugc-ads` |
| "Full brand campaign across paid + email + social" | `higgsfield-cmo-agent` |
| "60-day content factory with 100 videos" | `higgsfield-content-factory` |
| "Single 5-8s product clip" | `seedance-pipeline` direct |
| "Static product image only" | `selrai-ad-image` |

**Hard divide vs `higgsfield-ugc-ads`:** that skill is the
*script-driven multi-chunk* path. This skill is the *URL-driven no-prompt*
path. Do not poach each other's triggers.

---

## Inputs The Skill Asks For (Confirm-Before-Building Gate)

Before any credit-burning render, the skill confirms a 5-field intake:

1. **Product URL**. must have rich landing-page copy. Marketing Studio
   reads the page and silently builds the brief. Bare product pages with
   only a name + price scrape badly. Coach the user to point at the
   richest version (long-form description, hero copy, benefits block).
2. **Campaign goal**, `awareness` / `conversion` / `retention`. Drives
   format mix (see "Format selection rules" below).
3. **Avatar choice**, `default` / `custom_mint` / `soul_id_<name>`.
   Default is the fastest path but the default library is *saturated*
   (same faces appear in everyone's ads). Custom mint via text prompt is
   the recommended quality bar. Soul ID is for repeat campaigns where
   the same on-camera face must persist.
4. **Iteration tier**, `cheap_test` (2-clip UGC + CTA only, 720p) or
   `full_stitch` (5-clip, 1080p). Always recommend `cheap_test` first.
5. **Output destination**. defaults to
   `~/board/_active/marketing-studio-<YYYY-MM-DD>/` if not specified.

If any field is missing, ask **once**. then proceed with defaults
(`conversion` / `custom_mint` / `cheap_test`) and tell the user what was
defaulted.

---

## Confirm-Before-Building Restatement

After intake, the skill must restate intent in 5 lines before touching
Marketing Studio:

```
Marketing Studio campaign:
  Product: <URL>
  Goal: <goal> → format mix: <UGC + Tutorial + Unboxing + Review + CTA>
  Avatar: <avatar choice>
  Tier: <cheap_test | full_stitch>, credits: ~<n>
  Output: <path>

Proceed? (y/n)
```

Wait for `y`. This costs zero credits and saves both money and a regen.

---

## Format Selection Rules (Goal → Mix)

Marketing Studio offers five formats: **UGC**, **Tutorial**, **Unboxing**,
**Product Review**. and **UGC Try-On Haul**. The CTA clip is generated
separately (5s, no format dropdown, it's a direct Seedance prompt).

| Goal | Recommended mix (full_stitch) | Cheap test |
|------|------------------------------|-----------|
| Awareness | UGC (hook 15s) → Tutorial (demonstrate 15s) → CTA (5s) | UGC + CTA |
| Conversion | UGC (hook 15s) → Tutorial (15s) → Unboxing (10s) → Review (15s) → CTA (5s) | UGC + CTA |
| Retention | Unboxing (10s) → Tutorial (15s) → Review (15s) → CTA (5s) | Review + CTA |
| Try-on haul (fashion) | UGC (15s) → Try-On Haul (15s) → Review (15s) → CTA (5s) | Try-On + CTA |

**Why this mix:** the 5-clip conversion stitch is the THE ECOM KING 4.6x
ROAS recipe, it compounds hook (UGC) + demonstrate (Tutorial) + proof
(Unboxing) + social-proof (Review) + action (CTA) into the structure paid
ads need. A single 15s UGC clip is not enough for cold traffic.

---

## Avatar Strategy (Read This Before Picking)

Default avatars saturate. Higgsfield ships a small library of pre-built
faces, they appear in everyone's ads as more people use Marketing Studio.
By month 6 of using defaults, your ads look the same as your competitor's.

**Recommended ladder:**

1. **First time using the skill**. custom mint via text prompt. Click
   *Create* under Avatars, choose *Generate from text*, describe the
   avatar (age, gender, vibe, ethnicity). 1 minute, ~50 credits, gives
   you a face nobody else has.
2. **Repeat campaigns for same brand**. convert your custom mint into a
   Soul ID (see `higgsfield-soul`). This locks the face permanently and
   gives you the same character across Marketing Studio + direct Seedance
   + Cinema Studio.
3. **Founder/creator personal brand**, Soul ID of the founder's actual
   face. Best authenticity, requires 5-10 reference photos.
4. **Last resort**. default avatar, only if iterating fast and the
   campaign is throwaway.

**Never upload a real person's photo without their permission.** This is
a hard rule, not a Higgsfield rule. See `higgsfield-soul` for consent
template.

See `prompts/04-avatar-strategy.md` for the full decision tree.

---

## The Workflow (Step By Step)

The skill walks through 5 prompts in sequence. Each prompt is a separate
file under `prompts/` so you can iterate on them individually.

### Step 0, Setup gate (always)

Before anything:

- Confirm Higgsfield MCP is connected (run `ToolSearch` with query
  `higgsfield`). If not, point the user at `higgsfield-apps` to install.
- Confirm workspace is set to a Marketing Studio-enabled workspace via
  `higgsfield-workspaces`.
- Confirm credits balance (Plus plan = $49/mo minimum, 5-clip stitch
  burns ~5x a single Seedance render).
- Confirm output folder exists:
  `mkdir -p ~/board/_active/marketing-studio-<YYYY-MM-DD>/`

If any gate fails, fix it before proceeding. Do not start renders into a
broken workspace.

### Step 1, Product ingest (`prompts/01-product-ingest.md`)

- Paste product URL into Marketing Studio's Product tab.
- Wait 2-3 minutes for the system to scrape the landing page.
- Confirm the loaded product card shows correct name, image, price, and
  benefits. If anything is wrong, the scrape failed, point at a richer
  URL or use the manual product entry fallback.
- Save the scraped product card as a screenshot to
  `<output>/00-product-card.png`.

### Step 2, Format selection (`prompts/02-format-selection.md`)

- Apply the goal-to-mix table above.
- Confirm the final list of clips with the user (one line per clip,
  format + duration + role).
- If user wants to deviate, accept it but flag if the structure violates
  the hook → demonstrate → proof → social-proof → action shape.

### Step 3, Multi-format stitch render (`prompts/03-multi-format-stitch.md`)

- For each clip in the list:
  1. Marketing Studio → same product + same avatar selected.
  2. Swap format dropdown to the next format.
  3. Duration: 15s (10s for Unboxing).
  4. Resolution: 720p if `cheap_test`, 1080p if `full_stitch`.
  5. Click Generate. Wait 60-90s.
  6. Download MP4 to `<output>/clip-<n>-<format>.mp4`.
  7. Human gate before next clip, review the just-generated clip, only
     proceed if quality bar is met. If not, regenerate ONCE then accept
     and plan to cover in CapCut.
- For the final CTA (5s):
  - Use the prompt skeleton in `templates/cta-clip-prompt.md`.
  - Generate via direct Seedance (Marketing Studio has no CTA format dropdown).
  - Download as `<output>/clip-cta.mp4`.

### Step 4, Assembly + voice gate (`prompts/05-assemble-and-ship.md`)

- Hand the clip set to `../shared/capcut-finishing.md`:
  - Import clips in order.
  - Speed adjust each to 80-90% (AI rushes delivery).
  - B-roll overlay any hallucinated frames (head morphs, hand glitches).
  - Audio sync, mute any clip where the AI voiceover is unsalvageable
    and overlay the next clip's audio.
  - Auto-captions, Classic preset, brand color.
  - Export 1080p H.264 9:16.
- Write any on-screen text / caption / CTA copy via:
  - `content-engine` voice ship-gate (MANDATORY).
  - `humanizer` slop ship-gate (MANDATORY).
  - These run on the caption block, the CTA prompt, and any social copy
    that ships with the ad. Never skip, Marketing Studio's default copy
    fails Luke's voice grade about 80% of the time.
- Hand the final MP4 to `higgsfield-ad-critic` for post-render critique
  (hook strength, pacing, hallucination check, CTA legibility).

### Step 5, Ship + log

- Final MP4 at `<output>/final-ad.mp4`.
- Caption + CTA at `<output>/caption.md` (voice-graded).
- Cost log at `<output>/cost-log.md` (credits burned, regen count).
- Update `~/board/_log.md` with the campaign name + URL + spend.
- If the user is uploading to Meta Ads, hand off to `paid-ads` (campaign
  strategy) or `meta-ads-mcp-setup` (API connect). Do not auto-upload,
  that's a separate human gate.

---

## Avatar Consistency Across Clips

Marketing Studio's character-consistency algorithm holds the same face
across clips IF:

1. You pick the same avatar in the dropdown for every clip in the stitch.
2. You don't change the avatar mid-render (the previous clips are not
   re-rendered to match, you'll get a face swap mid-ad).
3. The format swap stays inside Marketing Studio (do not mix Marketing
   Studio clips with direct Seedance clips that use a different Soul ID
  , the eye color/jaw shape will drift).

If consistency drifts anyway, use the CapCut overlay trick: cover the bad
frame with a B-roll clip (unboxing footage works well) and mute the
audio. See `../shared/capcut-finishing.md` Fix 2.

For multi-campaign consistency (same face across this week's ad + next
week's ad), promote the custom mint to a Soul ID via `higgsfield-soul`.

---

## Element Tagging (Optional, For Product Consistency)

If the product also needs to be exactly identical across clips (not just
visually similar), tag the product via `../shared/element-tagging.md`:

- Pre-render a clean hero shot of the product (white background).
- Upload to Higgsfield Elements panel, tag it `@product`.
- Marketing Studio will composite the exact asset wherever `@product`
  appears in the auto-generated prompt.

This is overkill for most ecom products (the landing page scrape gives
Marketing Studio enough to render the product faithfully). Use Elements
tagging only when product visual fidelity is critical (e.g. unique
packaging, branded label, distinctive shape).

---

## Cost + Iteration Strategy

**Per-clip cost (Higgsfield credits):**

| Setting | Credits per 15s clip | Notes |
|---------|---------------------|-------|
| 720p, default avatar | ~75 | Cheapest |
| 720p, custom mint | ~100 | +25 for avatar mint (one-time) |
| 1080p, default avatar | ~150 | 2x the credits, marginal quality bump |
| 1080p, custom mint | ~175 | Recommended for final |

**Full stitch cost (5 clips at 1080p, custom mint):** ~875 credits ≈ $52
USD on Plus plan ($49/mo for 4000 credits = $0.012/credit).

**Iteration discipline (mandatory):**

1. Always render `cheap_test` first (2 clips, 720p, custom mint), costs
   ~200 credits ≈ $2.40. If the hook + CTA don't land, the full stitch
   won't either. Kill and reshape the brief before spending more.
2. Build the full 5-clip stitch only after `cheap_test` passes
   `higgsfield-ad-critic`.
3. Budget 30-50% failed-render overhead. Some clips will hallucinate and
   need one regen. If a clip needs 3+ regens, the format is wrong for the
   product, switch format (e.g. drop Unboxing if the product is digital).

**Plus plan ($49/mo) is the practical minimum.** Marketing Studio on the
free tier will let you generate 1-2 clips total. The 5-clip stitch
requires paid credits.

---

## Failure Modes (Named In Plain English)

| Symptom | Cause | Fix |
|---------|-------|-----|
| Product card loads with wrong name / no benefits | Landing page is thin (just name + price) | Point at a richer URL, long-form description page, hero copy block |
| Product card never loads (>5 min) | Marketing Studio scrape failed | Hard refresh, retry. If still fails, use manual product entry (upload product image + paste benefits) |
| Avatar face changes between clips | Wrong avatar selected for one of the renders | Re-render the bad clip with the correct avatar locked |
| Default avatars look generic / "AI-y" | You're using a pre-built library face | Mint custom avatar via text prompt, never upload a real person |
| Voiceover rushes through dialogue | Seedance 2.0 default speech pacing is fast | CapCut speed adjust to 80-90% |
| Head morphs / hands glitch in one frame | AI hallucination, ~5% of clips | B-roll overlay + audio mute (CapCut Fix 2) |
| 5-clip stitch feels disjointed | Hook → demo → proof → social → CTA shape broken | Re-check format order against the goal-to-mix table |
| Caption / CTA fails Luke's voice grade | Marketing Studio default copy is generic AI prose | Mandatory `content-engine` + `humanizer` pass before ship |
| Credits burning faster than expected | Skipped `cheap_test` step | Restart with cheap_test; pause full_stitch until cheap_test passes |
| MCP shows no Higgsfield tools | MCP not installed / wrong workspace | Run `higgsfield-apps` install ritual; check `higgsfield-workspaces` |

---

## Voice + Slop Gates (HARD RULE)

Every text artifact the user sees on-screen or in the caption MUST pass
through both gates:

1. `content-engine`, voice filter (Luke's verified house style).
2. `humanizer`, slop blocklist (banned vocab below + 21-category AI
   writing patterns).

**Banned vocab in this skill's outputs:** "game-changer", "10x", "crushing
it", "killing it", "secret sauce", "level up", "unlock", "transform".
Banned punctuation: em dashes (use commas or full stops).

No outcome guarantees. No "this will get you 10x ROAS." Process language
only: "stitched 5-clip ad ready to test", "ready to upload to Meta Ads",
"voice-graded caption ready."

If the skill emits text that fails either gate, the ship is blocked. Run
through both gates again, rewrite, then ship.

---

## Output Bundle

Every run produces a dated folder:

```
~/board/_active/marketing-studio-<YYYY-MM-DD>/
├── 00-product-card.png         (Marketing Studio scrape screenshot)
├── 00-brief.md                 (intake transcript: URL, goal, avatar, tier)
├── 01-format-list.md           (final 5-clip list with role + duration)
├── clip-1-ugc.mp4              (15s, hook)
├── clip-2-tutorial.mp4         (15s, demonstrate)
├── clip-3-unboxing.mp4         (10s, proof)
├── clip-4-review.mp4           (15s, social proof)
├── clip-cta.mp4                (5s, action)
├── final-ad.mp4                (CapCut stitch, 1080p H.264 9:16)
├── caption.md                  (voice-graded caption + CTA)
├── critic-report.md            (higgsfield-ad-critic output)
└── cost-log.md                 (credits burned per clip + total + regens)
```

This folder is the ship artifact. Hand it to the user as a single path ,
they upload `final-ad.mp4` + paste `caption.md` into their ad platform.

---

## Dependencies (What This Skill Calls)

| Skill | Why |
|-------|-----|
| `higgsfield-apps` | Marketing Studio is documented as an App. Install + workspace gate. |
| `higgsfield-workspaces` | Routes to the Marketing Studio-enabled workspace. |
| `higgsfield-soul` | Custom mint → Soul ID promotion for repeat campaigns. |
| `seedance-pipeline` | The Marketing Studio backbone. Used directly for the 5s CTA clip. |
| `../shared/higgsfield-prompt-skeletons.md` | CTA clip prompt template. |
| `../shared/capcut-finishing.md` | Stitch assembly (mandatory after render). |
| `../shared/element-tagging.md` | Optional `@product` consistency primitive. |
| `content-engine` | Voice ship-gate (MANDATORY on any caption / on-screen text). |
| `humanizer` | Slop ship-gate (MANDATORY). |
| `higgsfield-ad-critic` | Post-render critique pass. |

If `higgsfield-ad-critic` doesn't exist yet, the skill ships without the
critic step and logs a TODO to `<output>/critic-report.md`.

---

## Related Skills (Sibling Cross-Reference)

- `higgsfield-ugc-ads`, script-driven multi-chunk UGC. Use when the
  user has a written script or wants more control over the per-clip
  dialogue.
- `higgsfield-cmo-agent`, brand-brief-to-multi-channel campaign. Use
  when the deliverable is more than one ad (paid + email + organic + DM).
- `higgsfield-content-factory`, 60-day, 100-video production line. Use
  when the user is running a content engine, not a single campaign.
- `higgsfield-apps`, the catalog. Marketing Studio is one of many Apps.
- `higgsfield-soul`, character consistency primitive. Bolt on when
  running repeat campaigns with the same on-camera face.
- `seedance-pipeline`, direct Seedance render. Use when the user doesn't
  need a stitch (one 5-8s clip is enough).
- `selrai-ad-image`, static product image ads (no video). Use when the
  channel is image-only (Meta carousel cards, display ads).

---

## Example (Skincare Product, 45s Conversion Spot)

See `examples/sample-skincare-stitch.md` for a full worked example: a
skincare brand product URL gets ingested, the conversion mix is selected,
a custom female founder-style avatar is minted, 5 clips render, CapCut
stitches the final 45s spot, voice-graded caption ships. Total credit
spend ≈ 900 credits ≈ $11 USD on the Plus plan.
