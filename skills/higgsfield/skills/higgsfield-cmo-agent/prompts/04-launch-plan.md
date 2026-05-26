# Stage 4: 4-Week Launch Plan

Read `01-segments.md`, `02-channel-plan.md`, `03-creative-briefs.md`.
Output a single rollout calendar covering 4 weeks: Week 0 (pre-launch),
Week 1 (launch), Week 2 (sustain), Week 3 (optimise).

Owner column stays blank, the user fills it.

## Per-Week Structure

```markdown
## Week 0: Pre-launch (T-7 to T-1)

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|

## Week 1: Launch

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|

## Week 2: Sustain

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|

## Week 3: Optimise

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|
```

## Rules

1. **Each row is a single shippable thing.** Not "do influencer outreach".
   Instead "DM 12 nano-tier handles from segment 2 list".
2. **Fewer high-impact rows over filler.** A clean week beats a busy one.
   Aim for 4-8 rows per week, not 15.
3. **Reuse Stage 2 cross-segment leverage.** Call out which row is a
   re-cut of an earlier asset. E.g. "Re-cut of Day 1 Reel for LinkedIn
   (Segment 3)."
4. **Week 1 launch row anchors the campaign date.** For Selr workshop
   runs, the workshop day is the campaign anchor. Pre-launch counts back
   from there. Sustain and optimise count forward.
5. **Status column starts blank** so the user can track ship state.
6. **Owner column stays blank**, never assume team roles. The user
   knows their team better.
7. **Every row that requires copy ships gets a handoff stub** noting which
   skill produces it (`copywriting`, `email-content-engine`,
   `ad-creative`, `carousel-generator`, etc.). The launch plan does NOT
   generate the assets, it sequences them.

## Kill Criteria Footer (Mandatory)

After the 4 weekly tables, write a kill criteria section:

```markdown
## Kill Criteria

Three numeric thresholds at which we cut or pivot:

1. **[Specific metric]**, If [metric] < [threshold] by [day], then
   [action]. Example: "If CTR < 0.6% on hero Reel by Day 5, swap the
   headline and re-cut from B-roll."
2. **[Specific metric]**, Threshold + day + action.
3. **[Specific metric]**, Threshold + day + action.

If any kill criterion fires, do not "wait and see", execute the action
immediately. The campaign survives by killing fast, not by hoping slow.
```

**Kill criteria rules:**

- Must be numeric. "Engagement is low" is not a kill criterion.
- Must have a specific day to evaluate against. "By Day 5" not
  "eventually".
- Must name the action. "Pivot" is not an action. "Swap the headline
  and re-cut" is.
- 3 criteria total. Fewer and you've under-thought the failure modes.
  More and you've over-engineered.

## Selr AI Specifics

For Selr workshop campaigns:

- **Week 0** lands one carousel + one Reel teaser + open registrations.
- **Week 1** is the workshop week, launch Reel on Mon, attendee push
  Tue, workshop Wed, attendee recap Thu, Office Hours Thu evening.
- **Week 2** sustains with Skool conversion sequence (8-touchpoint
  workshop-to-Skool play from `workshop-to-skool-sequence.md`).
- **Week 3** optimises by re-cutting workshop B-roll for the NEXT city's
  pre-launch (compounding loop).

Anchor metric for Selr workshops: **workshop registrations** (target
varies per city). Anchor metric for Skool campaigns: **30-day Skool
conversion %** (target 40%).

Sample kill criteria for Selr Melbourne workshop:

1. If paid registrations < 30 by T-14 (Week 0 mid-week), kill paid ads
   and triple organic Reel frequency for Week 0 final 3 days.
2. If hero Reel CTR < 0.6% by Day 5 of Week 0, swap the headline and
   re-cut from existing workshop B-roll.
3. If workshop → Skool 30-day conversion < 40% by Day 21, review the
   close script (not the front-end), re-record the workshop-end Office
   Hours invite.

## Voice Gate (Mandatory Before Saving)

1. `content-engine`, strip slop, support promises, drop-in invites,
   outcome guarantees, em dashes, AU/US English mismatch.
2. `humanizer`, strip signs-of-AI-writing patterns.

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/04-launch-plan.md
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| 15+ rows in Week 1 | Cut to 6-8. Filler kills momentum |
| Row says "do outreach" | Specify, "DM 12 named handles" |
| Week 0 has no anchor date | Add the campaign date and count back |
| Kill criteria say "if engagement is low" | Force numeric, CTR %, registrations N |
| Owner column pre-filled with "Luke" | Blank it, user assigns |
| No handoff stubs on copy-shipping rows | Add `copywriting` / `ad-creative` / etc. note per row |
| Sustain week is identical to launch week | Sustain is lower-tempo follow-up + Skool conversion, not launch repeat |
| Optimise week ignores the next campaign | Re-cut Week 1 B-roll for the NEXT city's pre-launch |

## Demo Output (Selr AI Melbourne Workshop: 2026-06-12)

```markdown
# 4-Week Launch Plan: Selr AI Melbourne Workshop, 2026-06-12

Anchor date: Wednesday 2026-06-12 (workshop day).

## Week 0: Pre-launch (2026-06-05 to 2026-06-11)

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|
| Mon 06-05 | Hero Reel goes live (Segment 1, "You install it in the room") | IG @selr__ai | | |
| Mon 06-05 | LinkedIn text post, Luke shares workshop format breakdown | LinkedIn (Luke) | | |
| Tue 06-06 | Carousel ships, "5 ops bottlenecks the next Melbourne workshop installs", `carousel-generator` template = 5-tips | IG @selr__ai + LinkedIn | | |
| Wed 06-07 | Workshop registration email, 600 words, `email-content-engine` handoff | Email (Selr list) | | |
| Wed 06-07 | DM 12 micro-influencer handles from Segment 2 list (Stage 6) | IG + X DMs | | |
| Fri 06-09 | Re-cut hero Reel for X (Segment 2, build-in-public angle) | X (Luke) | | |
| Sun 06-11 | Last-call Reel + email, "12 seats / 4 left for Melbourne Wed" | IG + Email | | |

## Week 1: Launch (2026-06-12 to 2026-06-18)

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|
| Wed 06-12 | Workshop day, live in Melbourne | Live | | |
| Wed 06-12 | Workshop B-roll capture (Higgsfield ref shots optional) | In-room | | |
| Thu 06-13 | Attendee recap Reel, single attendee's install ships | IG @selr__ai | | |
| Thu 06-13 | Office Hours session (workshop-end invite warm) | Skool live | | |
| Fri 06-14 | LinkedIn essay, Luke recaps the room's installs (no names without consent) | LinkedIn (Luke) | | |
| Sun 06-16 | Carousel, "What we shipped in the Melbourne room", `carousel-generator` template = case-study | IG + LinkedIn | | |

## Week 2: Sustain (2026-06-19 to 2026-06-25)

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|
| Mon 06-19 | Skool conversion email 1, 8-touch sequence kicks off, `email-content-engine` handoff | Email (Melbourne attendees) | | |
| Wed 06-21 | Re-cut Reel from workshop B-roll, "behind the install", Segment 1 hero | IG @selr__ai | | |
| Thu 06-22 | Skool conversion email 2 + Office Hours invite | Email + Skool | | |
| Fri 06-23 | LinkedIn case post, Day 3 of one attendee's install going live | LinkedIn (Luke) | | |
| Sun 06-25 | Carousel, "3 installs from Melbourne attendees, day 11", `carousel-generator` template = stack-reveal | IG + LinkedIn | | |

## Week 3: Optimise (2026-06-26 to 2026-07-02)

| Day | Asset / Action | Channel | Owner | Status |
|-----|----------------|---------|-------|--------|
| Mon 06-26 | Workshop B-roll re-cut for NEXT city (Sydney) pre-launch hero Reel | IG @selr__ai | | |
| Wed 06-28 | Skool conversion email 3, final push for Melbourne cohort | Email | | |
| Fri 06-30 | Influencer outreach round 2, Sydney handles, using Melbourne campaign B-roll as reference | IG + X DMs | | |
| Sat 07-01 | LinkedIn essay, what worked / what didn't in Melbourne (operator-to-operator) | LinkedIn (Luke) | | |
| Sun 07-02 | Campaign retro, write to ~/board/_log.md, Skool conversion % vs 40% target | Internal | | |

## Kill Criteria

1. **Paid registrations**, If paid registrations < 30 by T-14 (2026-05-29),
   kill paid ads and triple organic Reel frequency for Week 0 final 3
   days. Re-evaluate at T-7.
2. **Hero Reel CTR**, If CTR < 0.6% on the Day 1 Mon hero Reel by Day 5
   (2026-06-09), swap the headline and re-cut from existing workshop
   B-roll. Re-evaluate at T-3.
3. **Workshop → Skool conversion**, If 30-day Skool conversion < 40% by
   Day 21 (2026-07-03), review the workshop-end close script (not the
   front-end), re-record the workshop-end Office Hours invite. Apply
   change to Sydney workshop two weeks out.

If any criterion fires, execute the action immediately. The campaign
survives by killing fast.
```

## Next Stage

Once `04-launch-plan.md` is saved and voice-gated, Stage 5 reads the
briefs + plan and writes the social posts with paste-ready Higgsfield
prompts.
