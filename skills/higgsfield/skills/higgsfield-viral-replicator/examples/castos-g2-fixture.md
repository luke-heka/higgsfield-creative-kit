# Fixture, Castos G2 Reviews (Path B Deterministic Fallback)

> Used when the live G2 scrape is blocked by Cloudflare and both Apify
> + `agent-browser` fail. Allows the Path B clustering step to run
> deterministically for on-camera demos and offline treatment testing.
> When this fixture is in use, `raw-reviews.json` is tagged
> `"source": "fixture", "reason": "<scraper block reason>"`.

---

**Source URL:** https://www.g2.com/products/castos/reviews
**Product:** Castos (podcast hosting + WordPress plugin)
**Sample size in this fixture:** 8 reviews (representative cluster, not
exhaustive)

These quotes are paraphrased from the public G2 page and condensed for
the demo. Verify and replace with actual scraped reviews when the live
scrape works.

---

## Sample reviews

### Review 1

- **Reviewer:** Verified User
- **Role:** Owner, marketing agency
- **Company size:** Small-Business (≤50)
- **Rating:** 5
- **What they like best:** "Castos handles the WordPress side better
  than anyone we've tested. The Seriously Simple Podcasting plugin
  pairs with the host like they were built to be one product, because
  they were."
- **What they dislike:** "Pricing entry point is higher than the
  bargain hosts. Worth it, but worth flagging."
- **Problems solving:** "Replaces a stitched-together stack: WP plugin
  + separate host + analytics tool. One bill, one login."

### Review 2

- **Reviewer:** Verified User
- **Role:** Course creator
- **Company size:** Solo
- **Rating:** 5
- **What they like best:** "Private RSS for paid members works on every
  plan. We tried building this with Memberstack and unlisted YouTube,
  it was a nightmare. Castos is the only host that treats this as a
  first-class feature."
- **What they dislike:** "Branding on the mobile app is light. I want
  my logo bigger."
- **Problems solving:** "Members actually listen now. Churn is down
  because the audio works in the player they already use."

### Review 3

- **Reviewer:** Verified User
- **Role:** CEO, podcast production agency
- **Company size:** Small-Business
- **Rating:** 5
- **What they like best:** "Unlimited shows on the agency tier.
  Per-show hosting was eating our margin alive on Buzzsprout. Switched
  14 shows in a weekend."
- **What they dislike:** "We'd love deeper white-label options."
- **Problems solving:** "Margin protection. Our cost per show went
  from $15 to under $4."

### Review 4

- **Reviewer:** Verified User
- **Role:** Director of internal communications
- **Company size:** Mid-Market
- **Rating:** 5
- **What they like best:** "Private podcasting that scales. We have 800
  employees and Castos handles the per-subscriber RSS without breaking
  a sweat. SSO on the premium tier sealed it."
- **What they dislike:** "Took some IT back-and-forth on the SSO
  setup. Worth it."
- **Problems solving:** "CEO wanted an internal podcast, IT killed
  Spotify-for-Business, no other host we tried could do private + SSO
  + audit logs."

### Review 5

- **Reviewer:** Verified User
- **Role:** Founder
- **Company size:** Solo
- **Rating:** 5
- **What they like best:** "I emailed the CEO and got a reply in two
  hours. That doesn't happen with Spotify or Libsyn."
- **What they dislike:** "Nothing major."
- **Problems solving:** "I needed someone in my corner. Indie hosting
  feels like indie hosting."

### Review 6

- **Reviewer:** Verified User
- **Role:** Producer
- **Company size:** Small-Business
- **Rating:** 4
- **What they like best:** "Audio plus video in one host. We were
  paying Wistia and Buzzsprout for the same show. Now it's one bill."
- **What they dislike:** "Web player customisation is lighter than I'd
  like."
- **Problems solving:** "Consolidated our stack. One CMS for both
  formats."

### Review 7

- **Reviewer:** Verified User
- **Role:** Marketing manager
- **Company size:** Mid-Market
- **Rating:** 5
- **What they like best:** "YouTube auto-republishing. We were manually
  re-uploading every episode to YT. That alone saves us 3-4 hours a
  week."
- **What they dislike:** "Wish the YT side had richer thumbnail
  customisation out of the box."
- **Problems solving:** "Discovery on YouTube. Our podcast now has a
  real second home and we didn't have to staff a video editor."

### Review 8

- **Reviewer:** Verified User
- **Role:** Coach
- **Company size:** Solo
- **Rating:** 5
- **What they like best:** "No overage fees. I came from a host that
  charged me $200 the month I went viral. Castos doesn't punish me for
  growing."
- **What they dislike:** ","
- **Problems solving:** "Predictable pricing. I can scale without
  dreading the bill."

---

## Pre-clustered themes (for verification)

The skill should rediscover these on its own. They're listed here so
the demo is verifiable:

1. **"I needed someone in my corner."**
   - Founder accessibility, support speed, indie ethos
   - Anchor reviews: 5 (founder), 1 (agency)
   - Suggested treatment: **A, talking-head reconstruction** (emotional
     theme, identity-led)

2. **"I wanted to grow without rebuilding my stack."**
   - Consolidation, multi-feature host, switch-cost economics
   - Anchor reviews: 1 (agency), 6 (producer), 3 (CEO), 7 (marketing
     manager)
   - Suggested treatment: **B, text-on-broll with VO** (technical
     theme, specific savings, B-roll proves the consolidation visually)

3. **"Don't punish me for growing."**
   - No overages, unlimited at every tier, predictable pricing
   - Anchor reviews: 8 (coach), 3 (agency CEO)
   - Suggested treatment: **C, side-by-side before/after** (switching
     theme, "I came from a host that charged me $200" begs a
     before-after split-screen)

---

## Use this fixture when

- The Apify G2 scraper has no usable actor or hits paywall
- `agent-browser` triggers the Cloudflare challenge ("Pardon Our
  Interruption", "Just a moment", "Checking your browser")
- You're testing the review-to-ad prompts offline
- The on-camera demo needs deterministic clusters
- You want to walk through all three treatments in one session (each
  pre-clustered theme maps to a different treatment)
