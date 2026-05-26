# DTC E-commerce Starter Pack, Brief

Preconfigured intake for the `higgsfield-ugc-ads` multi-chunk pipeline. This pack ships a 5-chunk mid-funnel-punchy script aimed at a physical-product DTC brand ($25–$120 AOV, supplement / skincare / apparel / home).

**How to use:** copy this file to `~/board/_active/ugc-ads-<YYYY-MM-DD>/06-brief.md`, replace every `{{VARIABLE}}` with the brand's own value, then feed it to the canonical Chat 2 production prompt. The character_lock + universal_directions blocks below are pre-filled to match the DTC avatar from the research doc.

---

## Variables the owner edits (5 fields, 3 minutes)

| Field | What it is | Example |
|-------|-----------|---------|
| `{{BUSINESS_NAME}}` | Brand name as it appears on the bottle/box | "Lumi Skin" |
| `{{PRODUCT_NAME}}` | Specific SKU | "Overnight Glow Serum" |
| `{{OFFER}}` | The price + shipping anchor | "$54 with free shipping over $75" |
| `{{HERO_BENEFIT}}` | The one outcome that wins the click, in plain words | "skin feels softer the next morning" |
| `{{BEFORE_PAIN}}` | The painful before-state the buyer recognises | "my skin felt tight and bumpy by lunchtime" |
| `{{AFTER_RESULT}}` | The specific noticed change | "by day four my cheeks stopped feeling rough" |
| `{{INGREDIENT_OR_MECHANISM}}` | The named "why it works" | "ceramides and 0.3% encapsulated retinol" |
| `{{SHIPPING_URL}}` | The CTA destination | "lumi.co/glow" |
| `{{PRODUCT_TAG}}` | Higgsfield Element tag for this SKU | `@bottle` or `@serum` |

Optional:
- `{{LOCATION}}`, only if the brand is location-specific. Most DTC = leave blank.

---

## campaign_name

```
{{PRODUCT_NAME}}, mid-funnel-punchy, 2026-05-26
```

---

## character_lock (DTC default avatar)

```yaml
age: "late 20s to mid 30s"
gender: "female"            # flip if product targets male buyers
appearance: >
  Real-looking woman in her late 20s, candid and natural, looks like a customer
  not a model. Shoulder-length hair slightly messy from sleep, bare or
  near-bare face, no makeup chair vibe. Casual at-home wardrobe, soft cotton
  pyjama top or oversized white tee. Slightly tired warm expression that
  reads as a real morning, not a performance.
voice: "Megan"              # Higgsfield Change Voice name, conversational
soul_id: null
reference_image_path: "01-character-ref.png"
```

If the product targets a male buyer, swap `gender` and rewrite `appearance` with: *"Real-looking man in his early 30s, candid and natural, looks like a customer not a model. Slightly tousled hair, light stubble, plain grey t-shirt, expressive but unforced face."*

---

## universal_directions (DTC bathroom-and-kitchen aesthetic)

```yaml
hair: >
  Shoulder-length brown, loosely framing the face, slightly messy from
  sleep, NOT styled. Same in every chunk.
application: >
  When the product is in frame, character holds it naturally at chest
  height, eyes flick to it then back to camera. No infomercial wave, no
  point-and-smile. Hand placement is relaxed, fingers wrap the bottle
  comfortably, label faces camera but not perfectly squared (slight
  angle reads as candid).
b_roll: >
  Soft natural morning light from a window at camera-right, no fill light,
  no key. Modern apartment bathroom OR kitchen counter, clean but lived-in
  (toothbrush in cup, fruit bowl, half-empty coffee). Shallow depth of
  field, background gently out of focus, 50mm equivalent.
ugc_realism_notes: >
  Selfie handheld, slight wobble, imperfect framing, candid, no studio
  look, micro-pauses in delivery, eyes sometimes flick down to the phone
  screen mid-sentence as if checking the framing. Sound is ambient room
  tone with kitchen or bathroom soft hum. Not a single perfect take.
```

---

## chunks (5-chunk mid-funnel-punchy)

```yaml
chunks:
  - id: 1
    role: hook
    voiceover: "{{BEFORE_PAIN}} until I started doing this every morning."
    runtime: 4
    product_tag: null
    framing: >
      Selfie handheld, eye-level, shoulders and face fill the frame.
      Character looks just slightly off-lens then snaps back to camera on
      the hook word.
    include_product: false

  - id: 2
    role: problem
    voiceover: >
      I'd tried three other things in this category, spent hundreds, and
      nothing actually changed.
    runtime: 6
    product_tag: null
    framing: >
      Selfie handheld, slightly lower angle, character glances off-camera
      at the bathroom counter behind her, mouth slightly tight.
    include_product: false

  - id: 3
    role: solution
    voiceover: >
      Then I picked up {{PRODUCT_NAME}} and used it the way it actually
      says on the box.
    runtime: 6
    product_tag: "{{PRODUCT_TAG}}"
    framing: >
      Slight pan as character reaches off-screen and brings the product
      into frame at chest height, label visible but not squared. Small
      smile starts at the corners of her mouth.
    include_product: true

  - id: 4
    role: proof
    voiceover: >
      Four days in, {{AFTER_RESULT}}. It's the {{INGREDIENT_OR_MECHANISM}}
      doing the work, not some miracle claim.
    runtime: 8
    product_tag: "{{PRODUCT_TAG}}"
    framing: >
      Medium close-up, character demonstrates real use (uncapping,
      applying, pumping onto the back of her hand). Direct eye contact
      with lens after the action. Confident, micro-smile.
    include_product: true

  - id: 5
    role: cta
    voiceover: >
      It's {{OFFER}} at {{SHIPPING_URL}}. Linked in bio.
    runtime: 4
    product_tag: "{{PRODUCT_TAG}}"
    framing: >
      Selfie handheld, product held up at chest height beside her face,
      direct eye contact with lens, soft smile, no infomercial energy.
    include_product: true
```

---

## final_cta

```yaml
final_cta:
  voiceover: >
    It's {{OFFER}} at {{SHIPPING_URL}}. Linked in bio.
  runtime: 4
  on_screen_url: "{{SHIPPING_URL}}"
```

---

## Product tag convention

- This pack uses `{{PRODUCT_TAG}}` as a placeholder. Pick a tag that names the SKU shape, not the brand: `@bottle`, `@serum`, `@jar`, `@pouch`, `@can`.
- Pre-render the product on a clean white background using Nano Banana 2: *"Generate a high quality render of this image against a white background. Keep the label sharp and centred."* Save to `00-product-still.png`, upload to Higgsfield Elements, tag.
- Chunks 1 and 2 must have the tag REMOVED from the Higgsfield Elements panel before rendering. Otherwise the model hallucinates the bottle into the hook.

---

## Compliance rules baked into this brief (read before editing)

- **No medical or cure claims.** This brief never says "treats", "cures", "fixes", "heals", "clinically proven". If you swap in copy, do not introduce those words. Meta and TikTok auto-reject ads with them for skincare and supplement categories.
- **No outcome guarantees.** Voiceover says "four days in, my cheeks stopped feeling rough", not "guaranteed results in four days".
- **AU + US English both acceptable for DTC.** Default to US English in this pack (skincare, supps lean US-first). Override with AU spelling only if `{{BUSINESS_NAME}}` is Australian.
- **No "shop now" closing card.** End on the product in hand, not a logo card. The closing CTA is voice + on-screen URL only.

---

## Hashtag pack (paste into the caption, not the video)

```
#tiktokshopfinds #skintok #productreview #smallbusiness #unboxing #foryou #{{BUSINESS_NAME_NO_SPACES}}
```

Swap `#skintok` for the actual sub-tok matching the product (`#supps`, `#hairtok`, `#cleantok`, `#cooktok`).
