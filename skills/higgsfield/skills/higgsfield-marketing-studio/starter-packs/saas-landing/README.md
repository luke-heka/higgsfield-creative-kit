# SaaS Landing Starter Pack

60-second how-to for the no-prompt Marketing Studio campaign on a SaaS / micro-SaaS / indie tool landing page. US English, indie-hacker tone, founder-led.

---

## What you get

A finished 45-50 second vertical ad stitched from 4 clips (UGC hook + Tutorial old-way + real product Demo + CTA), voice-graded caption, cost log. Ready to upload to Meta Ads, LinkedIn, or run as a Twitter/X video reply.

## What you need (under 60 seconds)

1. **A content-rich landing page URL**. Must include hero + features + pricing + social proof + at least 400 words of body copy. Bare splash pages with only "Sign up for early access" will NOT scrape into a usable brief.
2. **A campaign goal**. Default = `conversion` for free-trial signups. Pick `awareness` for a Product Hunt launch week, `retention` for feature-update pushes to existing users.
3. **~200 credits for cheap_test** OR **~750 credits for the 4-clip full stitch**. SaaS uses one fewer clip than DTC (no Unboxing, no Product Review), so the credit cost is lower.

## How long

- Cheap test: ~15 minutes (UGC + CTA only).
- Full stitch: 45 minutes (4 clips + CapCut assembly).
- Add 10-15 minutes if you record a real Loom for the Demo clip instead of generating it.

## The fields you edit in `brief.md`

1. **Landing page URL** (line 8 area). Paste your richest public marketing page (not docs, not pricing-in-isolation, not the app login).
2. **Avatar mint prompt** (line 49 area). Edit the bracketed bits for builder vibe (hoodie or tee, home office, laptop visible). If you have a founder face, use Soul ID instead.

Everything else has SaaS-tuned defaults.

## How to run it (3 steps)

1. Open `brief.md`, fill the URL and avatar mint prompt.
2. Open `prompts.md`, copy **Prompt 1** (cheap_test), paste into Claude.
3. After cheap_test passes the critic, copy **Prompt 2** (full_stitch). If the Demo clip can't be AI-rendered faithfully, the skill pauses and asks for a real Loom recording.

If your CTA needs work after Prompt 2, copy **Prompt 3** (CTA-only re-render).

## Known scrape failures (most common pack)

SaaS landing pages are the #1 failure category in Marketing Studio. The scraper does not handle:

- **Next.js / Astro / Vue / Svelte SPA landing pages** (content renders client-side, scraper sees an empty shell).
- **Cloudflare hard challenge** (scraper gets blocked at the edge).
- **Vercel preview URLs with password protection**.
- **Selrai-style domains and other custom-CMS landing pages**.
- **Splash pages with under 300 words of body copy** (no brief to extract).
- **Pages that gate the full content behind an email wall** ("Sign up to see more").

**Workaround (5 extra minutes):**

1. Screenshot your hero, feature block, pricing block, and social-proof block.
2. In Marketing Studio, open the Product tab and click "Manual entry".
3. Upload the hero screenshot. Paste:
   - Product name (your SaaS name)
   - "Price" = your entry tier (e.g. "$19/mo" or "Free trial 14 days")
   - 3 benefit bullets copied from your landing page
   - A 100-word pitch ("what this tool does, for who, why it beats the incumbent")
4. Save the manual-entry product card. Marketing Studio renders the same quality output.

For the Demo clip specifically: if direct Seedance can't reproduce your exact UI faithfully (most apps with custom design systems), record a 15s Loom of the real click flow yourself. **Faked demos are unrecoverable trust damage in the indie / dev market**, this is non-negotiable.

## SaaS-specific gotchas

- **Never fake the demo.** Indie Hackers, r/SaaS, and Hacker News will roast you publicly. Real screen recording or no demo.
- **No corporate jargon.** Banned in this pack on top of the global list: synergy, leverage, best-in-class, enterprise-grade, next-generation, cutting-edge, robust, seamless, "powered by AI".
- **No outcome math.** Indie buyers distrust "save 20 hours per week" and "10x your conversions". Show the demo, let the math be obvious.
- **Voice = honest and slightly nerdy.** Founder explaining to a friend, not marketer pitching at a stage.
- **Demo plays at 100% real speed.** Don't speed-adjust the demo clip in CapCut, the click flow IS the proof.

## Output

Everything lands in `~/board/_active/marketing-studio-saas-<YYYY-MM-DD>/`:

- `final-ad.mp4` (the ship asset)
- `caption.md` (voice-graded caption + relevant hashtags)
- `clip-1-ugc.mp4`, `clip-2-tutorial.mp4`, `clip-3-demo.mp4`, `clip-cta.mp4`
- `cost-log.md`
- `critic-report.md`

## When to come back to this pack

- New feature launch = new run (hook reframes around the new feature).
- New pricing tier = new run.
- Persona-specific landing page (e.g. `/for-developers` vs `/for-marketers`) = separate run with persona-tuned avatar.
