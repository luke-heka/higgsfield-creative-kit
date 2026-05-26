# Stage 5: Social Posts

Read `01-segments.md`, `02-channel-plan.md`, `03-creative-briefs.md`,
`04-launch-plan.md`. For each segment, write 5-8 posts. Each post is a
complete spec: caption + format + surface + Higgsfield prompt (where
applicable) + why-this-works.

## Per-Post Format

```markdown
### Segment N: Post M

**Surface:** [Instagram Reels / IG carousel / TikTok / YouTube Short /
X post / LinkedIn / Email teaser]
**Format:** [9:16 video, 7-15s / 4:5 carousel, 7 slides / 1:1 still /
15s vertical / etc.]
**Hook (first 1.5s of video, or first line of caption):**
[The exact hook line, voice-graded]

**Caption:**
[Full caption, voice-graded, ban-list applied. Include the CTA. No
hashtag spam, 3-5 hashtags max if any.]

**On-screen text (if video):**
- 0-1.5s: [text band]
- 1.5-4s: [text band]
- 4-8s: [text band]
- 8s+: [text band]

**Higgsfield prompt:**
[Full paste-ready prompt using image or video skeleton from
`templates/higgsfield-image-prompt.md` or
`templates/higgsfield-video-prompt.md`. For carousels, this field says:
"Carousel → carousel-generator (template: <template-name>). Higgsfield
supplies slide 4 or slide 7 background only if requested." For X /
LinkedIn text-only, this field says: "Text-only, no Higgsfield prompt."]

**Why this works for this segment:** [One sentence anchored to the
creative brief's big idea + the segment's buying trigger.]
```

## Distribution Rules (Per Segment)

- **60% concept-driven** posts (anchored to the creative brief's insight)
- **30% utility** posts (how to use / what fits / where it goes)
- **10% brand POV** posts (founder voice, position-taking)
- **At least 1 single-take, no-cut shot** per segment (gives Higgsfield
  image-to-video an anchor it can run on without seam issues)
- **At least 1 named A/B-testable CTA** per segment (e.g.
  "Comment WORKSHOP for the city list" not "DM for info")
- **At least 1 carousel post** per segment IF the segment lives on IG or
  LinkedIn (hand off to `carousel-generator`)
- **Format mix per segment:** at least 40% video formats (Reels / Shorts
  / TikTok), the rest split across carousel / still / text-only

## Format-Specific Higgsfield Handoff

Use this decision tree per post:

| Format | Higgsfield prompt? | Skeleton | Notes |
|--------|---------------------|----------|-------|
| 9:16 video (Reel / Short / TikTok) | YES | Video Skeleton 2 | 5-8s per chunk, ONE action |
| 1:1 or 4:5 static still | YES | Image Skeleton 1 | Match aspect to destination surface |
| 16:9 long-form thumbnail | YES (still) | Image Skeleton 1 | Thumbnail only, body shot separately |
| 4:5 IG carousel | NO |, | Hand off to `carousel-generator`. Note template choice |
| LinkedIn carousel (PDF style) | NO |, | Hand off to `carousel-generator` |
| X text-only post | NO |, | Text only, no visual asset |
| X thread | NO |, | Text only, Higgsfield not relevant |
| LinkedIn text-only post | NO |, | Text only, no visual asset |
| Email subject + body | NO |, | Hand off to `email-content-engine` for body |
| Podcast guest pitch | NO |, | Text only, Stage 4 launch plan row |

For carousels, name the `carousel-generator` template:

- **5-tips**, 5 bullet points + CTA card
- **case-study**, Before/after format
- **myth-bust**, Myth vs Truth alternation
- **stack-reveal**, Tool stack by category
- **cheat-sheet**, 2x2 grid reference
- **mistakes**, Anti-pattern listicle
- **feature-spotlight**, Single-keyword spotlight
- **feature-update**, Cream cards with S-mark
- **skill-announce**, Purple gradient + terminal
- **skill-card**, Single-slide SKILL.md display
- **tips**, Photo-fullbleed tips
- **prompt-anatomy**, Two-column prompt teardown
- **metaphor-explainer**, Win-95 metaphor visuals
- **replace-this**, 8-slide highlighter-block
- **reel-cover**, 9:16 vertical reel cover

Pick the template that fits the post's job. If unsure, default to
`5-tips` for educational posts and `case-study` for proof posts.

## CTA Wiring (Community Drops)

For any CTA that drops a community asset (Notion page, GitHub repo,
free tool), pre-stage the GitHub → Notion → ManyChat pipeline via
`community-publishing-pipeline`. Note in the caption which keyword
triggers ManyChat:

```
Caption ending: "Comment 'WORKSHOP' and I'll DM you the city list +
install kit."
```

Where "WORKSHOP" is the ManyChat trigger keyword and "install kit" is
the Notion page that drops.

For non-community-drop CTAs (e.g. "register at workshop.selrai.com.au"),
no pipeline staging needed, just the direct URL.

## Hook Bank Integration

Use `../shared/hook-bank-100.md` as the hook source. Pick an archetype
that matches the segment's awareness level:

| Segment awareness | Hook archetypes |
|-------------------|-----------------|
| Problem-aware | Archetype 1 (Problem-Aware), Archetype 7 (Pain-Point Pattern Interrupt) |
| Solution-aware | Archetype 3 (Contrarian), Archetype 5 (Numbered List Tease) |
| Product-aware | Archetype 4 (Case Study Lead), Archetype 8 (Demo Tease) |
| Brand-aware | Archetype 9 (POV / Behind the Scenes), Archetype 10 (Voice / Position) |

Pull the hook, substitute the bracketed variables, then voice-grade
through `content-engine` (some hook patterns need rephrasing for Luke's
voice, no em dashes, no "game-changer", no outcome promises).

## Skill Handoffs

For each post:

- **DR-style hook captions** → `direct-response-copy` skill for the hook
  line
- **Volume + structure** → `alex-hormozi-content-method` for the
  4-block structure (Hook → Tension → Reveal → CTA) and the give-give-
  give-ask flow across the segment's 5-8 posts
- **Per-platform format / timing** → `social-content` skill (e.g. LinkedIn
  posts at 7am AU, IG Reels at 12pm AU, TikTok at 7pm AU)
- **Paid headline variants for the hero 3** → `ad-creative` skill (output
  6-8 headline variants per hero post for Meta / Google / LinkedIn)
- **Carousel handoff** → `carousel-generator` skill (note the template)
- **Email handoff** → `email-content-engine` skill (for any email teaser
  in this stage)

Each handoff is a NOTE in the post spec, not an inline render. Stage 5's
job is to spec the post; Stage 4's launch plan sequences when each
handoff happens.

## Voice Gate (Mandatory Before Saving)

1. `content-engine`, every caption, every hook, every on-screen text
   band.
2. `humanizer`, every caption + every on-screen text band.

Re-grade if either fails. Do not save a failing draft.

## Summary Footer (Mandatory)

After all posts, write:

```markdown
## Stage 5 Summary

**Asset count by format:**
- 9:16 Video (Reels / Shorts / TikTok): N
- 4:5 IG carousel: N
- LinkedIn carousel: N
- 1:1 or 4:5 static still: N
- X / LinkedIn text-only: N
- Email teaser: N

**Re-use map (which posts re-cut which):**
- Segment 1 Post 1 (hero Reel) → Segment 3 Post 2 (LinkedIn carousel)
- Segment 2 Post 3 (X thread) → Segment 1 Post 5 (caption re-use)
- ...

**Hero 3 for paid amplification:**
1. **Segment 1 Post 1**, Meta ads, 9:16 Reel asset. Headline variants
   needed from `ad-creative`.
2. **Segment 2 Post 2**, LinkedIn Sponsored Update. Headline variants
   from `ad-creative`.
3. **Segment 1 Post 4**, Meta ads (lookalike of workshop email list).
   Headline variants from `ad-creative`.

**Community drop CTAs (pre-stage via `community-publishing-pipeline`):**
- Segment 1 Post 3: keyword "INSTALL" → Notion page <slug> + GitHub
  repo <slug>
- Segment 2 Post 5: keyword "STACK" → Notion page <slug>
```

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/05-social-posts.md
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| All posts are carousels | Force format mix, at least 40% video per segment |
| Higgsfield prompts use em dashes | Re-grade. Replace with commas |
| CTAs say "DM for info" | Replace with named A/B-testable CTAs ("Comment WORKSHOP") |
| Hooks all match the same archetype | Vary hook archetypes across posts within a segment |
| Captions are 800 words each | Cut to 50-150 words for IG; longer for LinkedIn; shortest for X |
| Hashtag spam (10+ hashtags) | Cap at 3-5 |
| On-screen text repeats the caption | Use on-screen text to add tension or visual punch, not echo |
| Carousel posts have Higgsfield prompts | Replace with `carousel-generator` handoff note + template name |
| No A/B-testable CTAs | Add at least one per segment |
| All hero 3 are from Segment 1 | Spread across segments, at least 2 segments represented in hero 3 |

## Demo Post (Selr AI, Segment 1, Post 1)

```markdown
### Segment 1: Post 1

**Surface:** Instagram Reels (@selr__ai)
**Format:** 9:16 video, 12s, founder-talking-head with one B-roll cut

**Hook (first 1.5s):**
"You don't need another AI course."

**Caption:**
We've watched 200+ AU operators install one working AI workflow in our
workshop room this year. Not the start of a course. The whole thing.
By 5pm Wednesday in Melbourne, you walk out with it running.

Comment WORKSHOP for the city list and install kit.

#AISmallBusinessAU #SelrAI #MelbourneFounders

**On-screen text:**
- 0-1.5s: "You don't need another AI course."
- 1.5-4s: "You need a day where the thing gets installed."
- 4-8s: "12 operators. One install each. Ships by 5pm."
- 8-12s: "Comment WORKSHOP for the city list."

**Higgsfield prompt:**
[Paste-ready, using video skeleton from
`../shared/higgsfield-prompt-skeletons.md` Skeleton 2:]

12 seconds 9:16, medium close-up handheld, AU operator man in his early
40s mid-install on a beat-up MacBook with terminal visible, in a Selr AI
workshop room with 11 other operators around tables in soft focus
background, mid-morning side light through tall windows natural soft,
slight handheld drift forward over the duration no zoom, 50mm equivalent
shallow depth of field background gently out of focus, palette dark wood
table cream walls Selr purple notebook accent in lower right of frame,
fine film grain natural skin texture, audio: ambient workshop room tone
with a single Slack notification ping at second 9, product visibility:
Selr purple appears once as notebook spine in lower-right third of frame
for the full 12 seconds, EXCLUDE: drone shots tripod stability stock-photo
poses AI-glossy skin gradient backgrounds overlay text watermark hashtag
overlays neon AI-circuit aesthetic.

**Why this works for this segment:**
Anchors the brief's big idea ("you install it in the room") in a single
shot of someone literally installing, with an A/B-testable CTA that
funnels via ManyChat for the warm follow-up.
```

## Next Stage

Once `05-social-posts.md` is saved and voice-gated, Stage 6 reads the
segments + briefs + posts and builds the influencer army with personalised
DMs.
