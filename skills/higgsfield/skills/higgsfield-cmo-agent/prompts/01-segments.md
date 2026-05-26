# Stage 1: Audience Segments

You have `00-brief.md` loaded. Produce 3-5 audience segments with the
canonical structure below. Be specific. Reject lifestyle aesthetics. Flag
the REPEAT and AMPLIFIER segments explicitly.

## Rules

1. **Validate or rewrite the brief's ICP guesses.** Do not just restate
   them. If a guess is too broad ("AU SMB operators"), narrow it. If a
   guess is wrong, reject it and replace.
2. **Reject any segment that's a lifestyle aesthetic without a specific
   job-to-be-done.** "Adventure-curious urbanites" is not a segment.
   "Subaru-owning weekend hikers who buy gear once a year before a planned
   trip" is.
3. **Flag exactly ONE segment as REPEAT**, the most likely repeat
   buyer / re-purchaser / re-engaging member.
4. **Flag exactly ONE segment as AMPLIFIER**, the most likely word-of-mouth
   driver, the segment whose buying behaviour pulls other segments in.
5. **If two segments overlap >70%, merge them.** Two near-identical
   segments is a tell that the audience definition is too coarse.
6. **3-5 segments total.** Fewer if the brief is narrow. Never more
   than 5, past 5, you're padding.
7. **Selr AI runs**, AU English in segment names and copy. Use AU SMB
   sector language ("trades operators", "hospitality operators", not
   "blue-collar workers").

## Per-Segment Structure

Write each segment in this exact format:

```markdown
### Segment N: [Plain English name, not a buzzword]

**Demographic:** Age band, gender skew, region, household income range
(or business size + revenue for B2B).

**Psychographic:** What they believe about themselves, what they hate,
what they brag about. Concrete, not generic.

**Job-to-be-done:**
- Functional: One sentence, the practical thing this product does.
- Emotional: One sentence, the feeling this product produces.

**Where they live online:** 2-3 specific surfaces. NOT "outdoor content",
NOT "AI Twitter". Use named subreddits (r/smallbusiness, r/ausfinance),
specific Instagram hashtags (#smallbusinessaustralia), specific YouTube
creators they watch, specific podcasts they download, specific Discord or
Slack communities. If you can't name a specific surface, you don't know
the segment yet, go back.

**Where they live offline:** 1-2 physical contexts where the product would
plausibly be in-frame. (For B2B brands: their office layout, their tools,
their stand-up format.)

**Buying trigger:** The specific moment that makes them open the wallet.
Not "when they need it", name the moment. "Their bookkeeper resigns and
they have 2 weeks to onboard a replacement." "Their staff schedules
collide for the third week running." "They hit $40K revenue and realise
they're trading time for dollars."

**Why this brand wins for them:** 1-2 sentences. If you can't write this
confidently, the segment is wrong, rewrite or reject.

**Repeat-buyer or amplifier flag:** One of [REPEAT / AMPLIFIER / NEITHER].

**Sample messages they'd actually respond to:** 2-3 lines, voice-graded.
These are not final post copy, they're the message angle that earns a
double-take from this segment. Write in this segment's voice, not yours.
```

## Output Order

Output segments in **priority order, most strategic value first**. The
top segment is the one the campaign anchors on. The bottom segment is the
one you'd cut first if budget dropped.

## Mandatory Footer

End with a 1-paragraph "Segments we considered and rejected" section:

```markdown
## Rejected Segments

- **<Name>**, Why it was tempting + why it was wrong. One sentence.
- **<Name>**, Why it was tempting + why it was wrong.
- (2-4 rejections is healthy. Zero rejections means you didn't think hard
  enough.)
```

## Voice Gate (Mandatory Before Saving)

Run the segments through:

1. **`content-engine`**, 5-axis critic. Strip slop. Strip support
   promises, outcome guarantees, drop-in invites, personal life
   references. AU English check (Selr runs).
2. **`humanizer`**, strip Wikipedia signs-of-AI-writing patterns
   (inflated symbolism, promotional adjectives, vague attributions,
   rule-of-three overuse, AI vocabulary, negative parallelisms).
3. **Re-grade if either gate fails.** Do not save a failing draft.

## Output File

Write to `01-segments.md` in the output directory:

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/01-segments.md
```

## Failure Modes (Catch Before Saving)

| Symptom | Fix |
|---------|-----|
| 3 segments that are all "AU SMB operators" with minor twists | Merge them, find 2 genuinely distinct segments to replace |
| One segment is just demographic data with no JTBD | Reject. A segment without a JTBD is a census, not a segment |
| "Where they live online" says "Instagram" or "Reddit" | Force specifics, subreddit, hashtag, creator handle |
| Sample messages sound like agency pitch | Voice-grade fail, re-run through `content-engine` |
| Segment names use buzzwords ("Innovators", "Trailblazers") | Rewrite in plain English, "Operators with 5-15 staff who bought their first AI tool last quarter" |
| Zero rejected segments | You stopped thinking too early, name 2-4 cuts |
| Two segments both flagged REPEAT | Pick one. The flag is a strategic call, not a description |
| Segment that's a lifestyle aesthetic (e.g. "minimalist creatives") | Reject, no JTBD, no buying trigger |

## Selr AI Specifics

For Selr AI workshop campaigns, the canonical segment library to start
from (validate and rewrite, do not paste):

1. **AU SMB operators with a recurring ops bottleneck**, REPEAT (workshop
   → Skool conversion pipeline).
2. **Solo founders building AI agencies / consultancies**, AMPLIFIER
   (word-of-mouth in indie founder Slack / Discord / X).
3. **Mid-career operators repositioning into AI roles**, NEITHER (one-time
   workshop attendance, low Skool fit).
4. **Hospitality + trades operators (regional)**, REPEAT secondary
   (workshop → ASA pipeline if business size justifies it).
5. **Corporate AI champions inside larger orgs**, usually REJECT (wrong
   format for workshop, better fit for ASA-direct).

For Selr ASA campaigns, drop segments 2-4 and add:

1. **AU mid-market companies (20-200 staff) with internal ops complexity**
  , REPEAT.
2. **Founders who attended a Selr workshop and want the full install** ,
   AMPLIFIER (most credible referral source).
3. **Service businesses with manual back-office bottlenecks**, REPEAT.

For non-Selr brands, the library does not apply, derive segments from the
Stage 0 brief.

## Demo Output Sketch (Selr AI Workshop: Melbourne)

```markdown
# Audience Segments: Selr AI Melbourne Workshop, 2026-05-24

### Segment 1: AU SMB operators with a recurring ops bottleneck (REPEAT)

**Demographic:** 35-55, founders or COOs of 5-50 staff businesses,
revenue $1M-$10M AUD, mostly Melbourne metro + regional Victoria for this
campaign.

**Psychographic:** Sees themselves as competent operators who built the
business by hand. Hates buying training that's "just theory". Brags about
shipping fast and hiring slowly.

**Job-to-be-done:**
- Functional: Install one working AI workflow that removes a specific
  weekly bottleneck before adding the next.
- Emotional: Stop feeling like the bottleneck themselves.

**Where they live online:**
- r/smallbusinessAU
- LinkedIn AU founder commentary (Sam Wood, Romain Bonjean, etc.)
- The Australian Business Owners podcast network

**Where they live offline:** Their own office with the morning team
stand-up open on a whiteboard.

**Buying trigger:** They've watched a tool demo, realised they could
install it themselves with help, and want a deadline + room to do it.

**Why this brand wins for them:** Selr's workshop is the only AU offer
that puts the install in their hands in the room rather than handing them
a course they'll never finish.

**Repeat-buyer or amplifier flag:** REPEAT.

**Sample messages:**
- "You don't need an AI course. You need a day where the thing gets
  installed."
- "Workshop close: by 5pm Wednesday your inbox is triaging itself."
- "If you can run a Friday afternoon stocktake, you can run this."

(... segments 2-4 follow same format ...)

## Rejected Segments

- **Corporate AI champions inside enterprise IT**, Tempting because
  budget exists, but the workshop format is wrong for them; they want
  internal rollouts with security review, not a public-room build.
- **AI-curious students / early-career professionals**, No buying power
  for $1,500 AUD, no ops to install into, would dilute the room.
```

## Next Stage

Once `01-segments.md` is saved and voice-gated, Stage 2 reads it and builds
the channel plan per segment.
