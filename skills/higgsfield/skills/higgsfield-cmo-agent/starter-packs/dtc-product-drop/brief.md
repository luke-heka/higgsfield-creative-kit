# Starter Pack Brief: DTC Product Drop

> Preconfigured Stage 0 intake for `higgsfield-cmo-agent`. This is NOT a
> Selr AI run. Variables in `{{double-braces}}` are filled by the user at
> kickoff. Everything else is preset for the DTC e-commerce vertical.
>
> Source: industry research compiled 2026-05 (DTC ecommerce section).
> Voice rules below override the Selr ban-list, this pack uses casual
> visual-proof-led DTC voice in US English by default.

---

## Brand

- **Brand name:** `{{BRAND}}` (e.g. "Coastal Skin Co", "Heya Mug Co",
  "Lift Supps")
- **Category:** Physical DTC product. Skincare / supplement / apparel /
  drinkware / home goods. Sub-category captured at intake.
- **Founder (if relevant):** `{{FOUNDER_NAME}}` (optional; only needed if
  founder-led visual archetype is in the plan)
- **Voice:** Casual, conversational, visual-proof-led. Like texting a
  friend who tried it first. NOT polished brand copy.
- **Language:** US English by default (color, optimize, organization).
  Override to AU or UK at intake if the brand sells locally only.

## Hero Offer (This Campaign)

- **Product / drop:** `{{OFFER}}` (specific SKU or bundle)
- **Price:** `{{PRICE}}` (typical band $25-$120 AOV; bundles drive higher
  AOV; capture exact dollar figure at intake)
- **Format:** One-off launch / repeat drop / subscription / bundle
- **Drop date:** `{{LAUNCH_DATE}}`
- **Shipping offer:** `{{SHIPPING_OFFER}}` (e.g. "Free shipping over
  $75 US", default expectation in DTC)
- **Hero benefit:** `{{HERO_BENEFIT}}` (one specific outcome the product
  produces, e.g. "absorbs in 8 seconds, no white cast")

## Positioning One-Liner

`{{ONE_LINER}}`, fill at intake. Stage 0 prompts the user with three
formats to pick from:

1. "The `{{CATEGORY}}` for people who already tried `{{INCUMBENT}}`
   and it didn't stick."
2. "Made by `{{FOUNDER_NAME}}` after `{{ORIGIN_MOMENT}}`."
3. "`{{INGREDIENT_OR_MECHANISM}}` does the thing every other
   `{{CATEGORY}}` claims to do."

## Campaign Goal

**Launch + awareness drop.** Drive first-purchase volume in the
launch window, build retargeting audience from engaged viewers, set
up the repurchase / bundle ladder for cohort 1.

- **Anchor metric:** Units sold in launch window (`{{LAUNCH_DATE}}`
  +14 days)
- **Secondary metric:** AOV vs target threshold
  (`{{AOV_THRESHOLD}}`)
- **Tertiary metric:** Cost-per-acquisition stays under
  `{{CPA_CEILING}}` on Meta + TikTok

## ICP Guesses (To Validate in Stage 1)

The Stage 1 prompt will narrow these. Typical DTC segment shapes:

1. **Skeptical re-buyer**, REPEAT primary. Has tried 3+ products in
   the category, none stuck. Needs real-people proof, not brand claims.
   Buys when one specific person they trust says it actually worked.
2. **First-time category buyer (price-sensitive)**, AMPLIFIER. Searching
   for an entry point, finds your product via TikTok Shop or
   creator-driven Reel. High share-rate, low single-purchase value, but
   drives word-of-mouth to segment 1.
3. **Loyal-to-incumbent switcher**, NEITHER. Currently using
   `{{INCUMBENT}}`. Will only switch if the difference is concrete in
   the first 7 seconds of video. Hardest to convert, highest LTV when
   converted.

## Channel Emphasis (DTC Default)

Stage 2 builds the channel plan. Defaults for this vertical:

- **Primary:** Meta (Reels + Stories ads + retargeting) + TikTok
  (organic creator UGC + TikTok Shop + Spark Ads)
- **Secondary:** Email (cohort 1 retargeting, abandoned cart, post-
  purchase) + the brand's own IG feed for proof aggregation
- **Skip by default:** LinkedIn (no buyer fit), YouTube long-form
  (low ROI on launch window unless founder-led story is the brand)

## Visual Direction (Anchor)

- **Setting:** Real homes (bathroom, kitchen, bedroom, couch). Vanity
  counters. Front door / unboxing on bed. Phone-shot natively, never
  studio-set.
- **Subjects:** Real customers or look-like-customers, NOT models. Age
  band matches product (skincare 24-38 F-skew; supps 24-45 mixed;
  apparel 20-35 mixed). Messy hair allowed, no makeup chair vibe.
- **Lighting:** Natural window light or warm domestic interior. No
  studio strobes, no cinema 4K rigs (Meta + TikTok demote ads that
  look like ads).
- **Camera energy:** Phone on counter, phone in hand, selfie cam, or
  POV first-person. Vertical 9:16 always.
- **Color palette anchors:** Defaults to the brand's existing palette
  (captured at intake). Texture cues: phone-camera-real, soft grain,
  no plastic AI shine.
- **Product visibility:** HERO. Product in hand for 60%+ of frame
  time. Label readable. Brand insert pulled out and read on camera
  during unboxing.

## Voice Direction (Anchor)

- **Tone words:** casual, honest, slightly-tired-friend
- **Phrases to use:**
  - "I'll be honest"
  - "I tried it for `{{TIMEFRAME}}`"
  - "Here's what happens when..."
  - "Watch this"
  - "It's `{{HERO_BENEFIT}}`, that's the whole thing"
  - "I don't usually post about products but"
- **Phrases banned (DTC-specific):**
  - "Shop now" (in copy or end-card, kills native feel)
  - "Limited time offer" (DTC-cliché, lowers credibility)
  - "Game-changer" / "10x" / "next-level" (all banned universally)
  - Medical / cure claims for supps and skincare ("cures acne",
    "treats inflammation", "fixes hormones"), compliance trap on Meta
  - "AI-powered" anything (means nothing in DTC)
  - "Transform your skin" / "transform your body" (same energy)

- **Universal bans (apply across all packs):**
  - Em dashes
  - Outcome guarantees of any specific number
  - Refund / money-back / 30-day guarantee language in copy (the
    refund policy is on the product page, not in ads)
  - Personal life of operator / founder unless it's the brand origin
    moment captured at intake

## URLs

- **Store / PDP:** `{{STORE_URL}}` (e.g. "shop.coastalskinco.com")
- **Hero product page:** `{{PRODUCT_URL}}`
- **IG:** `{{IG_HANDLE}}` (e.g. "@coastalskinco")
- **TikTok:** `{{TIKTOK_HANDLE}}`
- **TikTok Shop link (if active):** `{{TIKTOK_SHOP_URL}}`
- **Discount code (for influencer + organic):** `{{DISCOUNT_CODE}}`
  (e.g. "DROP15" for 15% off launch week)

## Variables Captured at Intake

The Stage 0 prompt fills these in one batched ask:

| Variable | Required | Notes |
|----------|----------|-------|
| `{{BRAND}}` | Yes | Brand name as it appears on the bottle / label |
| `{{OFFER}}` | Yes | Specific SKU or bundle being dropped |
| `{{PRICE}}` | Yes | Single dollar figure or bundle band |
| `{{LAUNCH_DATE}}` | Yes | Drop date in ISO format |
| `{{HERO_BENEFIT}}` | Yes | The one outcome to lead every asset with |
| `{{BEFORE_PAIN}}` | Yes | What the customer was using before (the incumbent) |
| `{{AFTER_RESULT}}` | Yes | Specific observable change post-product |
| `{{INGREDIENT_OR_MECHANISM}}` | Optional | The "why this one" anchor |
| `{{FOUNDER_NAME}}` | Optional | Only if founder is on-camera |
| `{{SHIPPING_OFFER}}` | Yes | Free shipping threshold or flat rate |
| `{{AOV_THRESHOLD}}` | Yes | Target cart value for bundle math |
| `{{INCUMBENT}}` | Optional | The product they're switching from |
| `{{DISCOUNT_CODE}}` | Optional | Launch discount or influencer code |
| `{{TARGET_CONCERN}}` | Yes | Specific body / skin / use-case concern |

## Hashtag Pack (Starter)

5-7 hashtags Stage 5 will adapt per post:

- `#tiktokshopfinds`
- `#{{CATEGORY}}tok` (e.g. `#skintok`, `#supptok`, `#homefinds`)
- `#productreview`
- `#smallbusiness`
- `#unboxing`
- `#foryou`
- `#{{BRAND_HASHTAG}}` (brand-specific, e.g. `#coastalskinco`)

## Hard Constraints (DTC Vertical)

- **Never claim medical outcomes** for supplements or skincare. Words
  banned outright: "cures", "treats", "fixes", "heals", "reverses",
  "anti-aging" (FDA-coded in US), "clinically proven" without a real
  citation. Meta compliance will reject these.
- **Never use stock B-roll.** Every visual is shot-on-phone, vertical,
  native aspect. Cinema-look kills the algorithm.
- **No "shop now" end-card with logo.** End on the product or face.
- **No paid testimonials presented as organic.** FTC disclosure rules
  apply. If a creator was paid, the post says "ad" or "paid".
- **No before/after photos with altered lighting or filters.** Trust-
  killer if the brand grows past 50K followers and a Reddit thread
  catches it.
- **No celebrity look-alikes or AI-generated faces in product hero
  shots.** Customer photos only, real shoot or licensed UGC.

## Existing Assets (To Capture at Intake)

- Product photography (PDP-ready)
- Founder photo / video (if founder-led)
- Existing UGC library (creator content + customer tags)
- Email list size + segmentation
- Current ad-account state (Meta Pixel, TikTok Pixel, retargeting
  audiences)
- Past creator partnerships (for the kill-list step in Stage 6)

## Campaign Window Default

- **Pre-launch:** 7 days before drop (T-7 to T-1), teaser content,
  email warmup, creator outreach
- **Launch:** drop week (T+0 to T+6), paid spike, full UGC drop,
  influencer go-live
- **Sustain:** drop +7 to +14 days, UGC re-cuts, retargeting,
  abandoned cart sequence
- **Optimise:** drop +14 to +21 days, winning ad scaling, losing
  ad swaps, repurchase email

Total: 4 weeks ending ~3 weeks after `{{LAUNCH_DATE}}`.

## Demo Command (When This Pack Loads)

```text
Build me a complete multi-channel marketing campaign for the
{{BRAND}} {{OFFER}} drop on {{LAUNCH_DATE}}. Run all 8 stages
including the influencer army.
```

Expected output structure: same as standard `higgsfield-cmo-agent`
run, written to:

```
~/board/_active/cmo-agent-{{BRAND_SLUG}}-{{YYYY-MM-DD}}/
```

## Override Notes

- If the brand is AU-only, override `language` to AU at Stage 0.
- If the product has medical or supplement claims, surface compliance
  rules at Stage 0 and re-confirm the ban-list.
- If the brand has no existing UGC library, Stage 6 over-indexes on
  nano-tier creator outreach to seed the asset bank.
