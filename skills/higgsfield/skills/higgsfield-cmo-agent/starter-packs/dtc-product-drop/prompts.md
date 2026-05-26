# Starter Pack Prompts: DTC Product Drop

Three paste-ready prompts for the DTC vertical. Each one drops into
the `higgsfield-cmo-agent` pipeline at a specific stage with the brief
in this folder pre-loaded.

Variables in `{{double-braces}}` get filled from `brief.md` (most are
captured at Stage 0 intake). The pipeline reads `brief.md` first, then
applies these prompts to override or extend the default stage prompts
for the DTC vertical.

---

## Prompt 1: Campaign Skeleton Kickoff (Stage 0 to Stage 1 Dispatch)

Paste this when starting a DTC drop campaign. It loads the brief,
captures the launch-specific variables, and dispatches Stage 1 with
DTC-vertical priors baked in.

```text
Run higgsfield-cmo-agent using the DTC product drop starter pack at
~/.claude/skills/higgsfield/skills/higgsfield-cmo-agent/starter-packs/dtc-product-drop/brief.md

Capture these Stage 0 variables in one batched ask, then dispatch
Stage 1 immediately:

- Brand name ({{BRAND}})
- Hero product / SKU being dropped ({{OFFER}})
- Price ({{PRICE}}) and AOV threshold ({{AOV_THRESHOLD}})
- Drop date ({{LAUNCH_DATE}})
- Hero benefit, one specific observable outcome ({{HERO_BENEFIT}})
- What the customer was using before, the incumbent ({{INCUMBENT}})
- Ingredient or mechanism that earns the lead ({{INGREDIENT_OR_MECHANISM}})
- Founder name and on-camera willingness ({{FOUNDER_NAME}})
- Target concern, specific use-case or body/skin issue ({{TARGET_CONCERN}})
- Shipping offer ({{SHIPPING_OFFER}}) and discount code ({{DISCOUNT_CODE}})
- Existing UGC library: yes / no / partial
- Past creator partnerships to load into the Stage 6 kill list

Then run Stage 1 (Audience Segments) with these DTC priors:

1. Use US English by default. Override to AU only if the brand sells
   AU-only.
2. Lead with the skeptical re-buyer segment, flag as REPEAT primary.
3. The first-time category buyer is the AMPLIFIER if TikTok Shop or
   creator-driven discovery is in the channel mix.
4. Force "Where they live online" to name specific TikTok creators,
   subreddits (r/SkincareAddiction, r/Supplements, r/Frugal_Jerky), or
   Instagram hashtags the segment actually scrolls. NEVER generic
   "TikTok" or "Instagram".
5. Buying trigger must be one specific moment, not "when they need it".
   Example: "Their existing serum runs out, they're staring at the
   Sephora wall, the regular reorder feels like settling."
6. Apply the DTC ban-list from brief.md: no medical claims, no "shop
   now" copy, no "transform", no game-changer language, no celebrity
   look-alikes in references.

Output to:
~/board/_active/cmo-agent-{{BRAND_SLUG}}-{{YYYY-MM-DD}}/

Pause after Stage 1 and surface the segments + the rejected segments
footer for review before dispatching Stage 2.
```

---

## Prompt 2: DTC Creative Brief Variant (Stage 3 Override)

Paste this when you reach Stage 3 and want the DTC-specific creative
brief format. Overrides the default Stage 3 prompt with DTC visual
archetypes and the phone-shot-not-studio anchor.

```text
Run Stage 3 of higgsfield-cmo-agent (Creative Briefs) for the
{{BRAND}} {{OFFER}} drop using the DTC vertical override.

Read 01-segments.md and 02-channel-plan.md from the campaign output
directory. Write ONE creative brief per segment using the standard
format with these DTC-specific anchors:

**Big idea constraint:**
Every big idea is a single observable outcome the viewer can see
happen on camera. Not "{{HERO_BENEFIT}}" stated abstractly, but the
literal moment the product does the thing.

Example: NOT "{{HERO_BENEFIT}} is real". YES "The serum absorbs
before the camera can pan from the dropper to the cheek".

**Insight constraint:**
The insight paragraph names the EXACT moment the segment loses trust
in DTC ads. For the skeptical re-buyer, this is when a brand says
"clinically proven" without showing the proof. For the first-time
buyer, it's when the founder reads off a teleprompter instead of
holding the product up.

**Visual direction (locked for DTC):**
- Setting: real home, vanity counter, kitchen counter, bedroom,
  couch, front door for unboxing. NEVER a studio set, NEVER a styled
  shoot with a stylist credit.
- Subject: real customer or look-like-customer 24-38, age band matched
  to product. Messy hair allowed. No makeup chair vibe. If founder is
  on camera, founder is in casual at-home wardrobe, not branded merch.
- Lighting: natural window light, warm domestic interior light. No
  strobes. No 4K cinema rigs. Phone-camera native.
- Camera energy: phone propped on stand, phone in hand, selfie cam, or
  POV first-person. ALWAYS vertical 9:16.
- Color palette: pull from the existing brand palette, the product
  label, and the customer's actual home. Texture is phone-real with
  soft grain.
- Product visibility: HERO. Product in hand for 60%+ of frame time.
  Label readable in at least 3 seconds of the asset.

**Voice/copy direction (locked for DTC):**
- Tone words: casual, honest, slightly-tired-friend
- Phrases to use: "I'll be honest", "I tried it for {{TIMEFRAME}}",
  "Watch this", "Here's what happens when...", "I don't usually post
  about products but..."
- Phrases banned: "shop now", "limited time", "game-changer", "10x",
  "transform", "cures", "treats", "fixes", "heals", "AI-powered",
  "clinically proven" (without real citation), any em dash.

**Do (DTC-specific):**
- Show the product doing the thing in real time, no cuts.
- Show the label clearly for at least 3 seconds.
- Cite a specific number ({{PRICE}}, {{SHIPPING_OFFER}}, or
  {{TIMEFRAME}}) verbatim.
- Use a specific competitor name ({{INCUMBENT}}) when relevant. Real
  brands beat hypothetical "other products".
- Lead with the visual demo, not the founder talking head, unless the
  segment specifically responds to founder-led content.

**Don't (DTC-specific):**
- Use a studio-set or cinema-lit shoot.
- Use stock B-roll, stock music beds, or stock voiceovers.
- Stack 3 product shots in a row, breaks the native feel.
- Show before/afters with altered lighting, filters, or composition.
- Run "shop now" as an end-card with logo.
- Use AI-generated faces or celebrity look-alikes in product hero.

**Reference clues (composition only, NOT brand names):**
- A 30-second TikTok shot on a bathroom counter, side-light through a
  bathroom window, product squeezed onto the hand, no cuts, ASMR-loud
  product sound.
- An unboxing POV from a bed with messy sheets, phone selfie, brand
  insert pulled out and read on camera.
- A vanity-counter close-up of the product dispensing onto a cotton
  pad with the dropper visibly working.

**Throughline footer:**
After all per-segment briefs, write the throughline. For DTC, the
throughline almost always names: (a) the shared moment the segment
loses trust in DTC ads, (b) the shared visual anchor (phone-real,
domestic interior, product hero), and (c) the shared voice mark
(slightly-tired-friend honesty).

Apply the voice gate (content-engine + humanizer) before saving.
Output to 03-creative-briefs.md in the campaign directory.
```

---

## Prompt 3: DTC Influencer DM Variant (Stage 6 Override)

Paste this when you reach Stage 6 and need DTC-tier creator outreach
DMs. Overrides the default Stage 6 DM template with DTC-vertical
norms (creator code + product seeding + repost-rights ask).

```text
Run Stage 6 of higgsfield-cmo-agent (Influencer Army) for the
{{BRAND}} {{OFFER}} drop using the DTC vertical DM override.

For each handle in the tier tables, write a personalised DM following
this DTC 6-beat shape (modified from the default 5-beat). Max ~80
words per DM (DTC creators expect slightly more context than B2B).

**6-beat DTC DM shape:**

1. **Earned opener.** One specific thing from their recent content,
   ideally a post in the same product category. NOT "love your
   content". YES "Your {{SPECIFIC_RECENT_POST}} was the only review
   that made me actually try {{CATEGORY_PRODUCT}}".

2. **The brand in one line.** No CV-dump. ONE sentence that names
   what the product does + what makes it different. Example: "We
   make {{OFFER}}, the {{CATEGORY}} that {{ONE_LINER_DIFFERENTIATOR}}."

3. **Concrete ask.** Format + length + posting window + product
   integration. Example: "Would love to send a {{OFFER}} for an
   honest review, no script, your voice. One Reel, your usual length,
   posting between {{LAUNCH_DATE}} and {{LAUNCH_DATE+7}}."

4. **What's in it for them.** Specific. Product + creator code +
   commission rate OR flat fee + product. NOT "compensation TBD".
   Example: "Free product (no obligation to post), your own creator
   code {{CODE_NAME}} earning 15% on every sale through your link,
   plus flat $200 if you do post."

5. **Repost rights ask.** DTC-specific. Whether the brand can re-cut
   the creator's content for paid Meta or TikTok ads. Example: "If
   it's a fit, we'd ask for 90-day repost rights to re-cut for paid
   social. Standard for DTC, but happy to chat if that doesn't work."

6. **Easy out.** One line that gives them a clean way to say no.
   Example: "If timing's off or you're locked into another product
   in the category, no stress."

**Voice rules (DTC-specific):**

- No "Hey [first name]!", screams template
- No "we'd love to partner", means nothing in DTC
- No "passion" / "synergy" / "exposure"
- Emojis allowed sparingly if the creator's own voice uses them,
  otherwise skip
- Casual, founder-warm, not corporate. The DM should sound like the
  founder texting a friend.
- Sign off with the founder's first name + a single line of brand
  identity. Example: "Mia, founder of {{BRAND}}"
- US English by default (or AU/UK to match the brand's language
  setting from brief.md)

**Format per DM:**

```markdown
### DM: @handle (Tier: [macro/micro/nano], Platform: [TikTok/IG/YT])

[Full DM text, ready to send. Max ~80 words. Specific recent-content
reference. Concrete ask. Specific comp + creator code + commission
rate. Repost rights line. Easy out. Founder sign-off.]
```

**Per-handle brief, DTC version:**

After the DM, write the standard per-handle brief from the default
Stage 6 prompt, with these DTC-specific additions:

- **Product integration:** Where the product appears, how long it's
  on screen, whether the label is visible, whether the creator
  dispenses / uses the product on camera.
- **Demo requirement:** Yes / No. For DTC, demo-on-camera is usually
  required. Note exceptions.
- **Whitelisting:** Does the brand request paid amplification rights
  through the creator's handle? If yes, set the rate split now.
- **TikTok Shop tag:** If the brand has TikTok Shop active, require
  the product tagged in the creator's post for affiliate attribution.

Voice gate (content-engine + humanizer) every DM + every brief before
saving. Then run the GHL + Notion handoffs per the default Stage 6
flow. Output to 06-influencer-army.md.
```

---

## Notes on Using These Prompts

- Run prompt 1 first. It captures all the launch-specific variables
  and dispatches Stage 1.
- Run prompt 2 only when Stages 0-2 are complete (the brief and
  channel plan must exist for Stage 3 to override sensibly).
- Run prompt 3 only when Stages 0-5 are complete (the social posts
  drive the influencer content angle in Stage 6).
- All three prompts respect the universal ban-list (no em dashes,
  no refund promises, no outcome guarantees) PLUS the DTC-specific
  bans (no medical claims, no "shop now", no studio look).
- The voice gate runs on every stage regardless. Don't skip it.
