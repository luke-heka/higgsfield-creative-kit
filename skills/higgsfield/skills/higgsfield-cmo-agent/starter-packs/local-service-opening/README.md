# Starter Pack: Local Service Grand Opening

A preconfigured 8-stage campaign launch for a local trade or hospo
business opening up shop, a new service area, or a refurb relaunch in
a specific suburb.

Built on top of `higgsfield-cmo-agent`. Industry-specific voice,
compliance rules, and channel mix baked in for AU-default local
service operators (plumbers, sparkies, painters, hairdressers, cafes,
restaurants, mobile mechanics, locksmiths, lawn care, cleaners, etc).

---

## What you get out of one run

- 8 numbered documents under `~/board/_active/cmo-agent-{{BUSINESS-slug}}-{{YYYY-MM-DD}}/`
- A 14 to 28 day opening-window plan, channel by channel
- 5 to 8 ready-to-render reel scripts per ICP segment, each with a
  paste-ready Higgsfield video prompt
- A suburb-local micro-influencer outreach list with personalised DMs
  drafted for manual send (NEVER auto-sent)
- An aggregated Higgsfield prompt file you paste straight into the
  Higgsfield UI for the visual layer

## Fields you fill in (the bits that matter)

The full list lives in `brief.md`. The five fields that change every
run:

1. `{{BUSINESS}}`, your business name.
2. `{{TRADE_TYPE}}`, the specific trade or category (plumber, cafe,
   hair salon, etc.). Drives voice tone and visual archetype.
3. `{{SUBURB}}`, the primary suburb you want to win. This is the
   anchor for TikTok Local Feed targeting and most hashtag packs.
4. `{{LAUNCH_DATE}}`, opening day or relaunch day.
5. `{{BOOKING_LINK}}`, the online booking page. NEVER a phone number
   as primary CTA, even for trades.

Optional but high-leverage:

- `{{HERO_OFFER}}`, the specific opening-window offer (free safety
  check, first-coffee combo, first-cut discount, no call-out fee).
- `{{SIGNATURE_OFFER}}`, the lead dish, lead service, lead job-type
  the visual prompts will showcase.
- `{{VOICE_TONE}}`, blokey trade / warm hospo / warm personal
  services. Drives the script voice across all 8 stages.

## What it costs

- Documents only (Stages 1-6 + 8): $0. Pure Claude / writing work.
- Stage 7 aggregated prompts: $0 to produce, the prompts themselves
  are paste-ready text.
- Optional Higgsfield renders downstream (if you actually render the
  Stage 5 reels): roughly 28-42 credits per reel on Seedance 2.0 at
  720p. A full launch with 6 reels = 170-250 credits. Ultra plan
  monthly allotment is 3,000 credits, so a single opening campaign is
  a fraction of one month.

## What it takes

- 15-25 minutes to run all 8 stages once the brief is filled in.
- Per-stage human-gated. You can stop after Stage 1 (segments) or
  Stage 3 (creative brief) if you only want planning. Stages 5 and 6
  are where the bulk of the writing happens.

## When to use this pack instead of writing the brief yourself

- You are opening a new shopfront, new vehicle on the road, second
  chair, refurb relaunch, or expanding service area into a new suburb.
- You want a complete launch campaign in one sitting, not a single ad.
- You want the compliance rails (no fake response times, no fake
  reviews, no identifiable customer property in visuals, no
  phone-only CTAs) baked in by default.

## When NOT to use this pack

- You only need one reel or one ad. Use `higgsfield-ugc-ads` directly.
- You want a 60-day evergreen content plan (not a launch). Use
  `higgsfield-content-factory` instead, in the local-service variant.
- The business is national / online-only and not anchored to a
  suburb. Pick the DTC or SaaS starter pack instead.
- You are running a Selr AI workshop or running for Selr AI itself.
  This pack is industry-facing, not Selr-facing. The Selr AI brand
  defaults stub is the right path for that.

## How to invoke

In a fresh Claude Code session, paste:

```text
Use the higgsfield-cmo-agent starter pack at higgsfield-cmo-agent/starter-packs/local-service-opening/ for {{BUSINESS}}, a {{TRADE_TYPE}} in {{SUBURB}}. Filled variables below.
```

Then paste the filled-in variables block from `prompts.md` Prompt 1.

## Output structure (after a full run)

```text
~/board/_active/cmo-agent-{{BUSINESS-slug}}-{{YYYY-MM-DD}}/
00-brief.md                # filled-in copy of this pack's brief
01-segments.md             # 3 to 4 ICPs with flags + rejected footer
02-channel-plan.md         # TikTok Local + IG + GBP + FB groups
03-creative-briefs.md      # owner-on-site archetypes + voice
04-launch-plan.md          # 4-week rollout, kill criteria
05-social-posts.md         # 5 to 8 reels per segment + captions
06-influencer-army.md      # suburb micros + personalised DMs
07-higgsfield-prompts.md   # paste-ready aggregated visual layer
```

Plus the optional handoffs:

- GHL contacts tagged with the influencer outreach list (Stage 8a)
- Notion campaign page with DMs drafted for manual send (Stage 8b)
- ManyChat link refresh via `community-drop` (Stage 8c, only if the
  business is also running an IG DM funnel)

## Hard rules this pack enforces (so you do not accidentally break trust)

- No specific response-time promises in copy or voiceover.
- No identifiable customer property in any visual prompt.
- No phone-only CTAs.
- No "best in suburb" claims without proof in frame.
- No food stock footage in hospo prompts.
- No fake reviews, no inflated review counts, no "award-winning"
  claims unless the actual award is pictured.
- AU English throughout by default.

Break any of these and the suburb word-of-mouth flywheel breaks
faster than the campaign can run.
