# Segment Card: Template

Canonical per-segment data shape. Used by Stage 1 (segments) and
referenced by Stages 2-6 when they need to look up a specific segment's
fields.

## Segment Card Schema

```yaml
segment_name: "Plain English name, not a buzzword"
segment_number: 1
priority_rank: 1   # 1 = most strategic value, lower = cut first

demographic:
  age_band: "35-55"
  gender_skew: "60/40 male"
  region: "Melbourne metro + regional VIC"
  household_income: "N/A (B2B, replace with business size)"
  business_size: "5-50 staff"
  revenue_band: "$1M-$10M AUD"

psychographic:
  self_belief: "Competent operators who built the business by hand"
  hates: "Buying training that's 'just theory'"
  brags_about: "Shipping fast and hiring slowly"

job_to_be_done:
  functional: "Install one working AI workflow that removes a specific weekly bottleneck"
  emotional: "Stop feeling like the bottleneck themselves"

where_they_live_online:
  - "r/smallbusinessAU"
  - "LinkedIn AU founder commentary (Sam Wood, Romain Bonjean, etc.)"
  - "The Australian Business Owners podcast network"

where_they_live_offline:
  - "Their own office with morning team stand-up open on a whiteboard"

buying_trigger: "They've watched a tool demo, realised they could install it themselves with help, and want a deadline + room to do it"

why_this_brand_wins: "Selr's workshop is the only AU offer that puts the install in their hands in the room rather than handing them a course they'll never finish"

repeat_amplifier_flag: "REPEAT"   # one of [REPEAT / AMPLIFIER / NEITHER]

size_guess:
  total_addressable: "~50K AU SMB operators in this band"
  reachable_per_campaign: "~2K via existing Selr channels + paid"
  realistic_workshop_seats_filled: "8-12 per Melbourne workshop"

painpoints:
  - "Have bought 2-3 AI courses, didn't finish them"
  - "Have a bookkeeper or ops manager already, can't justify another full-time hire"
  - "Their staff schedule keeps colliding, they're patching it manually"

sample_messages:
  - "You don't need another AI course. You need a day where the thing gets installed."
  - "Workshop close: by 5pm Wednesday your inbox is triaging itself."
  - "If you can run a Friday afternoon stocktake, you can run this."
```

## Markdown-Rendered Format (For Stage 1 Output)

The YAML above is the data model. Stage 1's output file uses this
markdown-rendered format (matches Hewitt's structure, Selr-adapted):

```markdown
### Segment N: [Plain English name]

**Demographic:** Age band, gender skew, region, business size + revenue.

**Psychographic:** What they believe about themselves, what they hate,
what they brag about.

**Job-to-be-done:**
- Functional: One sentence.
- Emotional: One sentence.

**Where they live online:** 2-3 specific surfaces.

**Where they live offline:** 1-2 physical contexts.

**Buying trigger:** The specific moment that opens the wallet.

**Why this brand wins for them:** 1-2 sentences.

**Repeat-buyer or amplifier flag:** [REPEAT / AMPLIFIER / NEITHER]

**Sample messages they'd actually respond to:** 2-3 lines, voice-graded.
```

## Required Fields (Won't Pass Stage 1 Without These)

- `segment_name`, plain English, not buzzword
- `priority_rank`, for output order
- `job_to_be_done.functional` AND `job_to_be_done.emotional`, both
- `where_they_live_online`, at least 2 SPECIFIC surfaces (not "Reddit")
- `buying_trigger`, specific moment, not "when they need it"
- `why_this_brand_wins`, confidently written, or reject the segment
- `repeat_amplifier_flag`, must be set

## Optional Fields (Nice to Have)

- `size_guess`, quantifies the segment for prioritisation calls
- `painpoints`, feeds Stage 5 caption hooks
- `sample_messages`, feeds Stage 5 caption drafts

## Validation Rules

| Rule | Why |
|------|-----|
| `segment_name` cannot contain buzzwords ("Innovator", "Trailblazer") | Plain English forces clarity |
| `where_they_live_online` must contain at least one named surface (subreddit, specific creator, specific podcast) | "Instagram" is not a surface |
| `buying_trigger` cannot start with "when they" | Generic, force a specific moment |
| `repeat_amplifier_flag` is one of [REPEAT, AMPLIFIER, NEITHER] | Enforced enum |
| Only ONE segment in a campaign can have `repeat_amplifier_flag: REPEAT` | Strategic call |
| Only ONE segment in a campaign can have `repeat_amplifier_flag: AMPLIFIER` | Strategic call |
| `sample_messages` voice-graded through `content-engine` | Universal Selr ban-list applies |

## Stage Cross-Reference

| Stage | Uses these fields |
|-------|-------------------|
| 1, Segments | All fields |
| 2, Channel Plan | `where_they_live_online`, `priority_rank` |
| 3, Creative Briefs | `job_to_be_done`, `psychographic`, `painpoints` |
| 4, Launch Plan | `priority_rank`, `repeat_amplifier_flag` (for sequencing) |
| 5, Social Posts | `painpoints`, `sample_messages`, `buying_trigger`, `where_they_live_online` |
| 6, Influencer Army | `where_they_live_online`, `psychographic` (for niche fit scoring) |
| 7, Aggregator |, (mechanical reformat) |

## See Also

- `prompts/01-segments.md`, Stage 1 prompt that generates these cards
- `prompts/03-creative-brief.md`, Stage 3 reads these to build briefs
- `prompts/06-influencer-army.md`, Stage 6 reads these for creator fit
