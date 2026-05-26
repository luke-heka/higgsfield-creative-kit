# Course Creator Starter Pack

60-second how-to for the no-prompt Marketing Studio campaign on a coach / course creator sales page. Warmer voice, story-led, never income-claimy.

---

## What you get

A finished 45-50 second vertical ad stitched from 4 clips (UGC hook + Tutorial framework + Story proof + CTA), voice-graded caption, cost log, and a compliance-checked critic report. Ready to upload to Meta Ads, TikTok, or Instagram Reels promotion.

## What you need (under 60 seconds)

1. **A long-form sales page URL** for your course, cohort, or program. Stan Store / Kajabi / Teachable / custom landing pages all work IF the page has full sales copy (curriculum, testimonials, founder bio, pricing). Lead-magnet opt-in pages and Linktrees do NOT work.
2. **A campaign goal**. Default = `awareness`. Coach audiences need 7-21 touchpoints before buying, so awareness ads grow the warm pool. Switch to `conversion` only during a cohort cart-open window.
3. **~200 credits for cheap_test** OR **~750 credits for the 4-clip full stitch**.

## How long

- Cheap test: ~15 minutes (UGC + CTA only).
- Full stitch: 45 minutes (4 clips + CapCut assembly).
- Add 10 minutes for the compliance restatement gate (this pack has the strictest voice rules of all three).

## The fields you edit in `brief.md`

1. **Sales page URL** (line 8 area). Paste your richest long-form sales page.
2. **Avatar mint prompt** (line 53 area). Edit the bracketed bits for elevated-casual coach vibe. If you have a Soul ID of the real coach face, use that instead, personal-brand pull beats synthetic avatars in this category.

Everything else has coach-tuned defaults.

## How to run it (3 steps)

1. Open `brief.md`, fill the URL and avatar prompt.
2. Open `prompts.md`, copy **Prompt 1** (cheap_test), paste into Claude.
3. After cheap_test passes the critic + compliance gates, copy **Prompt 2** (full_stitch). If you have a real client willing to be on camera for clip 3, swap in real footage.

If your CTA flags any compliance check after Prompt 2, copy **Prompt 3** (CTA-only re-render).

## Known scrape failures (and the workaround)

Most coach sales pages scrape OK because the category lives or dies on long-form copy. Failure modes:

- **Stan Store / Kajabi / Teachable pages behind a custom domain redirect** (scraper follows the redirect to a different content shape).
- **Sales pages with auto-playing video as the hero** (scraper grabs the video metadata, misses the body copy).
- **Webinar funnel pages with thin top-of-funnel copy** (the offer detail lives behind a registration gate).
- **Lead-magnet opt-in pages** (no offer detail to extract).
- **Linktrees** (too many links, no offer focus).
- **Selrai-style domains and other custom-CMS pages**.

**Workaround (5-10 extra minutes, default for high-ticket):**

1. Copy the FULL sales page text into a doc (yes, all of it).
2. Take a hero screenshot showing the course mockup + headline + founder photo.
3. In Marketing Studio, open the Product tab, click "Manual entry".
4. Upload the hero screenshot. Paste:
   - Product name = course / cohort / program name.
   - "Price" = $X one-time OR $X x N payment plan.
   - 3 outcome-bullet benefits (process language only, NEVER income).
   - A 200-300 word excerpt covering: who this is for, what the framework is, what students walk away knowing how to do.
5. Save the manual-entry product card.

For high-ticket programs ($5K+), manual entry often outperforms the scrape because you can hand-pick the strongest 300 words from a 4,000-word sales page.

## Course-creator-specific gotchas (the strictest pack)

This pack has the most non-negotiable rules of the three:

- **NO income claims.** Banned: "$10K/mo", "6-figure", "7-figure", "$X in N days", any revenue number tied to a buyer outcome. Meta auto-rejects and FTC actively prosecutes.
- **NO outcome guarantees.** Banned: "guaranteed transformation", "you will [outcome]", "results in 30 days", "100% success rate". Process language only.
- **NO refund or money-back language.** Refund offers attract cheeky buyers gaming the offer.
- **NO rented luxury props.** No Lambo, no helicopter, no champagne-on-yacht. Trust-killer in 2026.
- **NO fake transformations.** Real clients only, with permission.
- **NO urgency manipulation.** Don't fake "limited spots" or "price goes up tomorrow".
- **NO drop-in invites.** Banned: "come say hi", "swing past", "if you're nearby".
- **NO casual support promises.** Banned: "DM me anytime", "weekly Q&A forever".

If any of these slip into the CTA dialogue, the skill blocks the render until you rewrite. Meta ad rejections cost hours; banned ad accounts cost months. The gate is non-negotiable.

## Voice tone

Warm, story-led, high-conviction. Like the coach is explaining their obsession to a smart friend at a coffee shop. Not corporate, not bro-y, not motivational-speaker. The 12-word avatar-naming hook ("If you've been [doing X] for [time] and still aren't [non-monetary outcome], here's why") outperforms every other hook in this category.

## CTA strategy

Lead-magnet CTA beats direct-sale CTA on coach audiences. Use:

- "Comment <KEYWORD> for the free framework."
- "Link in bio for the case study."
- "Tap below for the free walkthrough."
- "DM <KEYWORD> for the breakdown."

The buyer journey is awareness -> lead magnet -> email nurture -> sale. Don't compress it.

## Output

Everything lands in `~/board/_active/marketing-studio-course-<YYYY-MM-DD>/`:

- `final-ad.mp4` (the ship asset)
- `caption.md` (voice-graded caption + hashtags)
- `clip-1-ugc.mp4`, `clip-2-tutorial.mp4`, `clip-3-story.mp4`, `clip-cta.mp4`
- `cost-log.md`
- `critic-report.md` (compliance + voice review)

## When to come back to this pack

- New cohort = new run (hook reframes around the cohort dates).
- New lead magnet = new run (CTA changes).
- Real client willing to film = re-run clip 3 with real footage (huge trust uplift).
