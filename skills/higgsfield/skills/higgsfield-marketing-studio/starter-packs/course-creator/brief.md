# Brief: Course Creator Starter Pack

Preconfigured Marketing Studio intake for a coach or course creator (low-ticket course $97-$497, cohort program $997-$2,997, high-ticket mastermind $5K-$25K). Warmer voice, story-led, never income-claimy. Fill the placeholders, paste into the skill.

---

## Field 1: Product URL

```
<PASTE COURSE / SALES PAGE URL HERE>
```

**URL pattern guidance:**

Coach and course sales pages can scrape well IF they're full long-form pages. Most do, because the category lives or dies on copy length. Look for:

- A clear headline + subheadline that name the avatar and the transformation.
- A "who this is for / who this isn't for" block.
- Curriculum / module breakdown (specific frameworks, not just topics).
- 2+ client story / testimonial blocks (with names, ideally photos).
- Pricing block (one-time or payment plan).
- A founder/coach bio block with their own story.

**Examples that scrape well:**
- `https://yourbrand.com/cohort` (long-form sales page for the cohort).
- `https://yourbrand.com/course` (low-ticket course sales page).
- `https://yourbrand.com/work-with-me` (high-ticket coaching sales page).
- Stan Store / Kajabi / Teachable sales pages with full landing copy.

**Examples that scrape badly (avoid):**
- A bare Calendly link (no copy).
- A lead-magnet opt-in page (no offer, just an email gate).
- A Linktree (too many links, no offer focus).
- A booking confirmation page.

If the only public page is short, the manual fallback (below) works fine, paste in the full sales page copy by hand.

---

## Field 2: Campaign Goal

```
awareness
```

**Default for course creators:** `awareness`. Most coach/course audiences need 7-21 touchpoints before they buy. The first ads should grow the audience and build credibility, not push directly to a sales page on day one.

**When to switch:**
- `conversion` if you've already warmed an audience and you're running a cohort cart open window with a deadline.
- `retention` if you're upselling existing course buyers into a higher-tier program (Tier 1 -> Tier 2 ladder).

---

## Field 3: Avatar Strategy

```
custom_mint (or Soul ID of the coach's real face)
```

**For coaches, founder face wins.** If the coach is willing to be on camera (real photos to mint a Soul ID), do that. Personal-brand trust pulls harder than a synthetic avatar in this category.

**If the coach is camera-shy or building a faceless brand, custom mint:**

```
A [age 28-45] [woman/man], [hair description, well-groomed but natural],
[skin tone], wearing [elevated casual: good t-shirt, blazer over tee, soft
knit, NO power suits], [home office with bookshelf / co-working / hotel
lobby / clean desk], warm soft natural light, slightly leaning in toward
the camera with engaged friendly expression, looks like a friend giving
you the unfair advantage, no studio gloss, no rented luxury props in
frame.
```

**Fill rules:**
- Vibe = elevated casual. Not power-suit, not gym clothes, not Wolf-of-Wall-Street energy.
- Setting = home office bookshelf, co-working space, walking outdoor, hotel lobby. NEVER rented Lambo, NEVER Zoom-grid look.
- Expression = high-conviction, slightly fast, like they're obsessed with the framework they're about to share.

**Avoid:** generic "guru" tropes (sunglasses, money fan, mansion). The 2026 buyer is trust-fatigued and these visuals trigger instant suspicion.

---

## Field 4: Format Mix

```
UGC (hook 15s) -> Tutorial (story / framework 15s) -> Story (proof / case study 15s) -> CTA (action 5s)
```

**Total duration:** 50s. We render Story via direct Seedance with a narrative storytelling prompt (Marketing Studio's `product_review` format works as a fallback but tends to feel salesy).

**Why this mix (coach-specific):**
- UGC hook: avatar selfie, "If you've been [doing X] for [time period] and still aren't [result], here's why." Names the avatar's exact situation in 12 words. Best save rate of any coach hook.
- Tutorial: avatar at desk teaches the framework name + the contrarian move ("Most coaches do X, I do Y because Z"). Receipts > promises.
- Story: avatar tells a 15s client story (no income claims), "She came to me 12 weeks ago [stuck pattern]. Today she [non-monetary transformation: confidence, energy, momentum]." If the coach has a real client willing to be filmed, swap in real footage here.
- CTA: warm, never urgent-pushy. "Comment <KEYWORD> for the free framework" or "Link in bio for the case study." Lead-magnet CTA outperforms direct-sale CTA on coach audiences.

**No Unboxing.** Physical-product format breaks the personal-brand feel.

**Cheap test mix:** UGC + CTA only.

---

## Field 5: Iteration Tier

```
cheap_test
```

Always start here. Coach hooks fail more than DTC because the avatar pain language is subtle (the coach knows their avatar, the algorithm has to learn). Test the hook + CTA before the full stitch.

---

## Field 6: Output Folder

```
~/board/_active/marketing-studio-course-<YYYY-MM-DD>/
```

---

## Course Creator Hard Rules (Voice + Compliance)

These are the most stringent of all three packs because the coaching category has the heaviest compliance and trust traps.

- **NO INCOME CLAIMS** anywhere. Banned phrases: "make $10K/mo", "6-figure", "7-figure", "$X in 30 days", "guaranteed income", any specific revenue number tied to a buyer outcome. Meta auto-rejects and FTC actively prosecutes.
- **No outcome guarantees** of any kind. Banned: "guaranteed transformation", "you will [outcome]", "results in 30 days", "100% success rate". Use process language only: "the framework we'll walk through", "the methodology we teach", "here's what students learn".
- **No refund / money-back / satisfaction guarantee language.** Refund offers attract cheeky buyers who game the offer. The conviction layer comes from transparent price + real testimonials + named framework, not refunds.
- **No rented luxury props.** No Lambo in driveway, no helicopter selfie, no champagne-on-yacht. Trust-killer in 2026.
- **No fake or unverified client transformations.** Real clients only, with permission. If you can't show real proof, show the framework, not a fake result.
- **No urgency manipulation.** Banned: "limited spots" (without a real cap), "price goes up tomorrow" (unless it actually does), "this is the last time I'll offer this" (unless it's true).
- **No drop-in invites.** Banned: "come say hi", "drop in", "stop by", "if you're nearby". Every unpaid chat displaces a paid call.
- **No casual support promises.** Banned: "I'm here if you need me", "DM me anytime", "weekly Q&A forever". Business-survival rule, support promises become 24/7 unpaid obligations.
- **No em dashes.** Use commas or full stops.
- **Banned vocab (global):** game-changer, 10x, crushing it, killing it, secret sauce, level up, unlock, transform.
- **Voice tone:** warm, story-led, high-conviction. Like the coach is explaining their obsession to a smart friend at a coffee shop. Not corporate, not bro-y, not motivational-speaker.

---

## Fallback: When the URL Scraper Fails

Most coach sales pages scrape OK, but failure modes include:

- Stan Store / Kajabi / Teachable pages behind a custom domain redirect.
- Sales pages with auto-playing video as the hero (scraper grabs video metadata, no copy).
- Webinar funnel pages with thin top-of-funnel copy.
- Lead-magnet opt-in pages without offer detail.
- Selrai-style domains and other custom-CMS pages.

**If the scrape fails:**

1. Copy the FULL sales page text into a doc (yes, all of it, the long-form copy IS the brief).
2. Take a clean hero screenshot of the page (course mockup, founder photo, headline visible).
3. In Marketing Studio, open the Product tab, click "Manual entry".
4. Upload the hero screenshot.
5. Paste:
   - Product name = course / cohort / program name.
   - "Price" = $X one-time OR $X x N payment plan.
   - 3 outcome-bullet benefits (process language, never income).
   - A 200-300 word excerpt of the sales page covering: who this is for, what the framework is, what students walk away knowing how to do.
6. Save the manual-entry product card.

The manual-entry path is the default for high-ticket programs because their sales pages are often long enough that pasting in the rich copy outperforms what the scraper extracts.

---

## Confirm-Before-Building Restatement

Before any clip renders, the skill restates:

```
Coach Marketing Studio campaign:
  Product: <URL or manual-entry name>
  Goal: awareness -> mix: UGC + Tutorial + Story + CTA (4 clips, 50s)
  Avatar: <custom_mint elevated-casual / Soul ID of <coach name>>
  Tier: cheap_test, credits: ~200
  Output: ~/board/_active/marketing-studio-course-<YYYY-MM-DD>/

  Hard compliance checks: NO income claims, NO outcome guarantees,
  NO refund language, NO rented luxury, NO urgency manipulation.

Proceed? (y/n)
```

Wait for `y`. The compliance restatement is non-negotiable, this category gets ads rejected fastest if voice slips.
