# Brief: SaaS Landing Starter Pack

Preconfigured Marketing Studio intake for an indie / micro-SaaS or B2B tool ($9-$499/mo, free trial or freemium). Indie-hacker tone, US English, founder-led. Fill the placeholders, paste into the skill.

---

## Field 1: Product URL

```
<PASTE LANDING PAGE URL HERE>
```

**URL pattern guidance:**

SaaS scrapes are the highest-failure category in Marketing Studio. The scraper needs a content-rich landing page, not a 6-word headline + signup form. Audit your page before pointing the skill at it:

- Headline + subheadline that name the use case in one sentence.
- 3+ feature blocks with screenshots or product mockups.
- A pricing block (tier names, monthly price, key inclusions).
- A "who this is for" or "before/after" comparison.
- A founder quote, build-in-public stat, or social-proof block (testimonials, X tweets, GitHub stars, MRR).
- Total copy on the page: 400+ words minimum. Most landing pages with under 300 words fail to scrape into a usable brief.

**Examples that scrape well:**
- `https://yourtool.com` (if the homepage IS the long-form landing page)
- `https://yourtool.com/for-<persona>` (vertical landing page with persona-specific copy)
- `https://yourtool.com/launch` (launch page with full feature breakdown)

**Examples that scrape badly (avoid):**
- A 1-screen splash page with "Sign up for early access" only.
- A docs site (`docs.yourtool.com`).
- Pricing page in isolation (`/pricing`) without the use case context.
- App login screen (`app.yourtool.com`).

**Industry-specific URL warning:** B2B SaaS with gated content (lead-gen funnels behind email walls) scrapes the gate, not the product. Point at a public marketing page.

---

## Field 2: Campaign Goal

```
conversion
```

**Default for SaaS:** `conversion`. SaaS buyers need to see the demo aha in 15s and the CTA in 5s. Awareness alone doesn't drive signups for indie tools where the founder is unknown.

**When to switch:**
- `awareness` if launching a brand-new tool with zero users and you're priming the audience first (Product Hunt week, Twitter launch).
- `retention` for a feature-update push to existing users (annual renewal, churn-save, feature reveal).

---

## Field 3: Avatar Strategy

```
custom_mint
```

**Always custom-mint for SaaS.** Default Higgsfield avatars look like glossy marketers, not builders. SaaS buyers (devs, ops people, indie founders) distrust glossy faces in tool ads.

**Custom mint prompt template (edit the bracketed bits):**

```
A [age 26-38] [woman/man], [hair description, often slightly messy or
casual], [skin tone], wearing [hoodie / plain tee / casual button-down,
NO suits], home office or coworking setting in background, laptop visible
or nearby, soft natural light from a window, looks like a builder not a
marketer, slightly tired-but-focused expression, no studio gloss, no
makeup chair vibe.
```

**Fill rules:**
- Vibe = builder, not corporate. Hoodie or plain tee, never blazer.
- Setting = home office, co-working, coffee shop, or a clean desk. NEVER a "team meeting in a glass-walled conference room" stock-photo look.
- Slightly nerdy energy beats slick energy for indie/dev audiences.

**Founder face exception:** if the SaaS is founder-led (build-in-public, indie hacker brand), train a Soul ID on the founder's real face instead. The personal-brand pull is bigger than any synthetic avatar can deliver. See `higgsfield-soul` for the consent + reference photo flow.

---

## Field 4: Format Mix

```
UGC (hook 15s) -> Tutorial (demonstrate 15s) -> Demo (product screen aha 15s) -> CTA (action 5s)
```

**Total duration:** 50s. Marketing Studio doesn't have a `demo` format, so we render Demo via direct Seedance with a screen-recording prompt (see Prompts file).

**Why this mix (SaaS-specific):**
- UGC hook: founder selfie or builder-vibe avatar, names the painful old way in 7 words ("If you're still doing X manually...").
- Tutorial: avatar narrates the "before this tool" workflow (multiple tabs, spreadsheets, Slack threads). Sets up the contrast.
- Demo: full-screen product capture, the click flow that delivers the aha. The 0:30-0:45 segment is where signup intent forms.
- CTA: direct, "Start the free trial, link below" or "Cancel <incumbent>, link below."

**No Unboxing, no Product Review.** Physical-product formats break the SaaS native feel. The proof in SaaS is the demo working, not the box opening.

**Cheap test mix:** UGC + CTA only (skips the demo, validates the hook + offer before burning the full stitch).

---

## Field 5: Iteration Tier

```
cheap_test
```

Mandatory first run. SaaS hooks fail more often than DTC hooks because the pain language is more abstract ("tool fatigue" vs "dry skin"). Validate the hook lands before the full stitch.

---

## Field 6: Output Folder

```
~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/
```

---

## SaaS Hard Rules (Voice + Native Feel)

- **No fake demos.** Indie Hackers, r/SaaS, and Hacker News will roast you if they find out. The demo clip must show the actual product, not a mockup.
- **No vague "AI-powered" claims** without showing what the AI does on-screen.
- **No outcome guarantees** (no "10x your conversion", no "save 20 hours per week"). Indie buyers distrust outcome math.
- **No corporate jargon**: banned in this pack on top of the global banned vocab: "synergy", "leverage", "best-in-class", "enterprise-grade", "next-generation", "cutting-edge", "robust", "seamless", "powered by AI".
- **No em dashes** (use commas or full stops).
- **Voice tone:** honest, slightly nerdy, no hype. Like the founder is explaining the tool to a friend on a video call. US English (this is the indie-hacker default, even for AU founders).
- **End on the demo screen or founder face**, not a logo card.

---

## Fallback: When the URL Scraper Fails

SaaS storefronts fail scraping more than any other category. Common failure modes:

- Next.js / Astro / Vue SPA landing pages where content renders client-side.
- Pages behind Cloudflare hard challenge or Vercel preview password.
- Selrai-style domains and other custom-CMS landing pages.
- Pages with less than 300 words of body copy.
- Pages that gate the full content behind a "Sign up to see more" wall.

**If the scrape fails:**

1. Take 3-5 screenshots: hero + feature block + pricing + social-proof + footer.
2. Open Marketing Studio Product tab, click "Manual entry".
3. Upload the hero screenshot as the product image.
4. Paste manually:
   - Product name (your SaaS name).
   - "Price" field = your entry tier (e.g. "$19/mo" or "Free trial 14 days").
   - 3 benefit bullets (copy directly from your landing page).
   - A 100-word description (your "what this tool does" pitch).
5. Save the manual-entry product card. Marketing Studio renders the same quality output as a clean scrape.

If the demo clip needs the actual product on screen, record a 15s Loom of the click flow yourself and feed it as a reference image to direct Seedance (see Prompts file, Prompt 2 demo clip).

---

## Confirm-Before-Building Restatement

Before any clip renders, the skill restates:

```
SaaS Marketing Studio campaign:
  Product: <URL>
  Goal: conversion -> mix: UGC + Tutorial + Demo + CTA (4 clips, 50s)
  Avatar: custom_mint (builder vibe, <one-line description>)
  Tier: cheap_test, credits: ~200
  Output: ~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/

Proceed? (y/n)
```

Wait for `y`.
