# Stage 2: Channel Plan

Read `01-segments.md`. For each segment, pick a channel mix. Lead with reach
efficiency, not channel novelty. Be honest about what a 1-2 person team can
ship every week without burning out.

## Constraints

1. **Maximum 2 primary channels per segment.** If a third can't be
   justified, don't add it. "Maybe LinkedIn too" is not justification.
2. **Every channel needs a content format.** "YouTube long-form how-to" is
   a format. "YouTube" is not.
3. **Cadence must be honest.** What a 1-2 person team can actually ship.
   "Daily Reels + weekly long-form + weekly carousel + monthly podcast"
   is fantasy. "3 Reels per week + 1 carousel per week" is real.
4. **Amplifier row goes last per segment.** That's where
   influencer / UGC / community plays land. Leave it concrete, not
   aspirational.
5. **Cross-segment leverage is mandatory.** A 4-6 line footer naming which
   formats cut once and re-use across segments.
6. **Selr AI runs**, IG (@selr__ai + @mr_heka) and LinkedIn are
   defaults. YouTube is selective. Twitter/X is dead for Selr, only use
   if segment specifically lives there (e.g. indie founder segment).
   Email = `email-content-engine` handoff.

## Per-Segment Table Format

For each segment from Stage 1, output a table in this exact shape:

```markdown
### Segment N: [name from Stage 1]

| Role | Channel | Format | Cadence | Why this fits |
|------|---------|--------|---------|---------------|
| Primary | [channel] | [specific format] | [honest cadence] | [1 sentence] |
| Secondary | [channel] | [specific format] | [honest cadence] | [1 sentence] |
| Amplifier | [channel] | [specific format] | [honest cadence] | [1 sentence] |
```

**Role definitions:**

- **Primary**, Where this segment first sees the brand. Max 2 rows.
- **Secondary**, Where this segment converts (mid-funnel). 1 row.
- **Amplifier**, Where the segment hears about the brand from others
  (influencer / UGC / community / referral). 1 row.

## Per-Channel Format Specificity

For each channel, name the format with enough detail that Stage 5 can
write posts for it without further questions:

| Channel | Acceptable format spec | NOT acceptable |
|---------|------------------------|----------------|
| Instagram | "9:16 Reel, 7-15s, founder-talking-head" | "IG" |
| Instagram | "4:5 carousel, 7 slides, save-bait" | "IG posts" |
| TikTok | "9:16 Reel, 15-30s, hook + reveal + CTA" | "TikTok" |
| YouTube | "16:9 long-form how-to, 10-15 min, screen recording + voiceover" | "YouTube" |
| YouTube Shorts | "9:16 Short, 30-45s, single tip with on-screen text" | "YT Shorts" |
| LinkedIn | "Text post + carousel, 1500 chars, story-led" | "LinkedIn" |
| X / Twitter | "Thread, 8-12 tweets, contrarian observation + proof" | "X post" |
| Email | "Welcome sequence, 5 emails, 1 every 2 days" | "Email" |
| Podcast | "Guest appearance on [named show], 45-60 min, audio-only" | "Podcasts" |
| Live event | "In-person workshop, full day, $1,500 AUD, max 12 attendees" | "Live event" |
| Direct mail | "Postcard, A6, hand-addressed, to local SMB owners list" | "DM" |
| Paid ads | "Meta ads, 9:16 Reels asset, conversion campaign, $X/day" | "Paid" |

If you can't write the format that specifically, the channel is wrong for
the segment, or you don't yet understand the segment.

## Cadence Reality Check

Run every cadence through this check:

| Stated cadence | Real-world feasibility (1-2 person team) |
|----------------|------------------------------------------|
| Daily Reels | Only if it's hook + clip from a single weekly long-form shoot |
| 3 Reels per week | Real, sustainable |
| 1 carousel per week | Real (carousel-generator does the heavy lift) |
| 1 long-form video per week | Hard but possible if scripted + batched |
| 1 long-form per month | Real, comfortable |
| Weekly podcast guest spot | Real if pre-booked, fantasy if cold pitch |
| Monthly newsletter | Real, comfortable |
| Daily LinkedIn post | Real only if 30-min batched-writing block daily |
| Daily X thread | Fantasy unless someone owns it full-time |
| 1 in-person workshop per month | Real |

If a stated cadence fails the check, downgrade or drop it.

## Cross-Segment Leverage Footer (Mandatory)

After all segment tables, write a 4-6 line section naming the leverage:

```markdown
## Cross-Segment Leverage

- One hero film cut three ways: 60s for YouTube, 15s for Reels, 9s for
  TikTok hook.
- The Stage 5 carousel for Segment 1 re-cuts as a LinkedIn text post for
  Segment 3 (same insight, different surface).
- The workshop room B-roll feeds Segments 1, 2, and 4, film once, use
  across the month.
- The micro-influencer DMs from Segment 2 (AMPLIFIER) double as warm
  intros for Segment 1's local-market push.
```

If you can't find 3-5 leverage points, your channel plan is probably too
fragmented across segments, go back to Stage 1 and check for over-
segmentation.

## Voice Gate (Mandatory Before Saving)

1. `content-engine`, strip slop, support promises, drop-in invites,
   outcome guarantees, em dashes, AU/US English mismatch.
2. `humanizer`, strip signs-of-AI-writing patterns.

## Skill Handoffs

For each channel listed, note in a comment which downstream skill produces
the assets (used in Stage 4):

- IG Reels / TikTok / Shorts → Stage 5 social-posts + Higgsfield prompts
- IG carousel → Stage 5 social-posts + `carousel-generator` handoff
- LinkedIn text post / carousel → Stage 5 social-posts (no Higgsfield)
- Email → Stage 4 launch plan row that says "email sequence ,
  `email-content-engine` handoff"
- Paid ads → Stage 5 hero-3 selection + `ad-creative` handoff
- Podcast → Stage 4 launch plan row that says "outreach to [named show]
  for guest spot"
- Live event → Stage 4 launch plan row that anchors the campaign date

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/02-channel-plan.md
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| 3+ primary channels per segment | Cut to 2. The team can't ship 3 primaries |
| "YouTube" or "Instagram" with no format | Force format spec, see table above |
| "Daily Reels" with no source-shoot plan | Downgrade to 3/week or batch from weekly shoot |
| No amplifier row | Add one, every segment has a word-of-mouth angle, even if it's "none yet, build it" |
| 5 segments × 3 primaries = 15 channels | Plan is fantasy. Re-think, most segments share channels |
| Cross-segment leverage footer says "all formats reusable" | Specifics, not slogans. Name the cuts |

## Demo Output (Selr AI Melbourne Workshop)

```markdown
# Channel Plan: Selr AI Melbourne Workshop, 2026-05-24

### Segment 1: AU SMB operators with a recurring ops bottleneck

| Role | Channel | Format | Cadence | Why this fits |
|------|---------|--------|---------|---------------|
| Primary | Instagram (@selr__ai) | 9:16 Reel, 15-30s, founder-talking-head | 4 per week (M/W/F/Sun) | This segment scrolls IG between bookings; Reels match their attention span |
| Primary | LinkedIn (Luke) | Text post, 800-1500 chars, operator-to-operator story | 3 per week | LinkedIn is where AU SMB founders post their own wins; same room |
| Secondary | Email (Selr list) | Long-form essay, 600-900 words | 1 per week | Their decision happens in inbox not feed |
| Amplifier | IG + LinkedIn referrals from Skool members | Comment-prompt Reels + member tagging | Built into every Reel CTA | Skool member operators in the same segment carry credibility |

### Segment 2: Solo founders building AI agencies (AMPLIFIER)

| Role | Channel | Format | Cadence | Why this fits |
|------|---------|--------|---------|---------------|
| Primary | X / Twitter (Luke) | Thread, 8-12 tweets, build-in-public | 2 per week | This segment lives in indie founder X |
| Primary | YouTube (@mr_heka) | 16:9 long-form, 15-20 min, full skill walkthrough | 1 per fortnight | Long-form trust-build, this segment buys after 30+ min watched |
| Secondary | Skool community | In-feed posts | Ambient | They're already there if they're members |
| Amplifier | Indie founder Slack / Discord cross-posts | Build-log + skill drops | Weekly | Word-of-mouth carrier for the workshop |

(... Segment 3 + Segment 4 ...)

## Cross-Segment Leverage

- One workshop room B-roll shoot → Reels for Segment 1, YouTube cutdowns
  for Segment 2, LinkedIn stills for Segment 3, podcast guest-shot
  promo for Segment 4.
- Skool member testimonial Reel → re-cuts as LinkedIn carousel + X thread.
- Workshop curriculum carousel → carousel-generator template (5-tips),
  re-used across IG + LinkedIn for all 4 segments.
- Skool Premium 3-month-lock-in explainer Reel → cuts for IG (Segment 1),
  X thread (Segment 2), LinkedIn essay (Segment 3).
- The Luke + Harvey founder-pair B-roll feeds every "made by humans"
  angle across all 4 segments.
```

## Next Stage

Once `02-channel-plan.md` is saved and voice-gated, Stage 3 reads
01-segments.md + 02-channel-plan.md and writes the creative briefs.
