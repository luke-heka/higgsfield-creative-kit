# Stage 6: Influencer Army

Read `01-segments.md`, `03-creative-briefs.md`, `05-social-posts.md`.
Build a tiered influencer plan (macro / micro / nano), over-indexing on
micro and nano (small-brand reality, especially for Selr).

After tables + DMs + briefs, hand off chosen handles to GHL (tagged
contacts) and Notion (campaign page) via the wired skills. Then write
the kill list.

## Per-Tier Structure

```markdown
## Tier: [Macro / Micro / Nano]

**Definition for this campaign:**
[Follower band] + [posting cadence assumption].
- Macro: 500K+ followers, 1-2 posts/week
- Micro: 25K-250K followers, 3-7 posts/week
- Nano: 1K-25K followers, daily+

**Why this tier (or why we're skipping it):**
[1-2 sentences. If skipping, explain why, usually budget or fit mismatch.]

| Handle | Platform | Niche fit (1-10) | Why they fit | Content angle for THIS brand | Risk flags |
|--------|----------|------------------|--------------|------------------------------|------------|
| @handle | IG / X / YT / TikTok | N | One sentence | The SPECIFIC thing this creator should make for the brand | Anything that could blow up |
```

## Table Rules

1. **6-10 handles per tier.** Fewer for macro if skipping that tier.
2. **Niche fit ≥7 or don't list them.** No "maybe" handles.
3. **Content angle is THE SPECIFIC THING** this creator should make.
   - NOT: "post a Reel about the workshop"
   - YES: "Behind-the-scenes 30s of the moment she opens her laptop and
     runs the GHL setup skill at 6am before staff arrive, tumbler in
     frame for 8 of 30s"
4. **Risk flags** = anything that could blow up, controversial past
   content, recent sponsor stack overlap, audience mismatch, anti-AI
   public stance, low engagement rate vs follower count, recent algorithm
   penalty.
5. **For Selr runs, over-index on AU creators.** US handles only if the
   campaign explicitly targets US audience. AU creators in trades, SMB
   ops, hospitality, finance, regional founders.

## Per-Handle DM (Mandatory)

After tables, write a personalised DM per listed handle. Use
`templates/outreach-dm.md` as the structural reference (5-beat shape,
max ~70 words, AU-adapted, no US influencer norms).

**5-beat shape:**
1. **Earned opener**, one specific thing from their recent content.
   Cite a post, a series, a phrase they used. NOT "love your stuff".
2. **Why we're a fit (one line)**, connect their audience or POV to one
   specific thing about the brand. No CV-dump.
3. **The ask, concrete**, what we want them to make. Format + length +
   posting window.
4. **What's in it for them**, comp framework, product, exclusivity, or
   distribution. Specific numbers or specific items, NOT "compensation
   TBD".
5. **The easy out**, one line that gives them a clean way to say no.
   Reduces friction, increases reply rate.

**Format per DM:**

```markdown
### DM: @handle (Tier: [macro/micro/nano], Platform: [IG/X/YT/TikTok])

[The actual DM text, ready to send. Max ~70 words. No template fill ,
each DM names something specific from the creator's recent work.]
```

**Voice rules (Selr-specific):**

- No "Hey [first name]!", screams template
- No "we'd love to partner", means nothing
- No "let's hop on a quick call", they haven't said yes yet
- No "passion" or "synergy" or "exposure"
- No emojis unless the creator's voice clearly uses them
- No hashtags
- AU voice, direct, dry. "Worth a chat?" not "Excited to connect!"
- Sign off with Luke or the team member sending. Not "Selr AI Team".

## Per-Handle Brief (Mandatory, 5-8 lines)

After all DMs, write a short brief per handle:

```markdown
### Brief: @handle

**Concept:** [The specific content angle from the table, expanded with
the creative-brief throughline applied.]

**Deliverables:** [Quantity + format + posting window. E.g. "1 Reel,
9:16, 30-45s, posted between 2026-06-05 and 2026-06-12."]

**Required brand cues:** [Product visibility, hashtag, link sticker,
@mention. E.g. "Selr purple notebook visible for 8s+; @selr__ai mention
in caption; link sticker to workshop.selrai.com.au; #SelrAI tag."]

**Compensation framework:** [Product-only / fee + product / fee +
commission / equity. PICK ONE. Specific numbers if known.]

**Usage rights:** [What the brand can re-cut and run as paid. E.g.
"Brand can re-cut + run as paid Meta ads for 90 days from posting date."]

**Approvals:** [What we'll review pre-post, OR "post first, no approval
needed" if it fits the creator's voice, recommended for nano-tier.]
```

## Kill List Footer (Mandatory)

Close with a kill list, handles you considered and explicitly cut, with
one-line reason each:

```markdown
## Kill List

- **@handle**, Cut because [specific reason]. E.g. "Anti-AI public
  stance in March 2026 thread; audience would push back on partnership."
- **@handle**, Cut because [specific reason]. E.g. "Recent sponsor
  stack includes 3 competing AI courses; audience saturation."
- **@handle**, Cut because [specific reason]. E.g. "Engagement rate
  1.2% on 80K followers, bought-follower signal."
- (2-4 cuts is healthy. Stops the user from circling back to these
  later.)
```

## Voice Gate (Mandatory Before Saving)

1. `content-engine`, every DM, every brief.
2. `humanizer`, every DM, every brief.

## Post-Stage Handoffs (Automated)

After the stage file is saved and voice-gated, run these handoffs in
sequence:

### 1. GHL Write (via `ghl-crm` skill)

For each listed handle (NOT kill list):

```
Create contact in GHL:
- Name: @handle (display name from platform if available)
- Source: "influencer-outreach"
- Tags: ["influencer", "tier-<macro|micro|nano>", "campaign-<brand-slug>-<date>", "city-<city-if-applicable>"]
- Custom field: content_angle = <brief concept>
- Custom field: dm_status = "drafted"
- Custom field: platform = <IG/X/YT/TikTok>
- Custom field: handle_url = <full URL to profile>
```

Use the GHL helper at `~/.claude/projects/-Users-luke/scripts/ghl` or
the `ghl-crm` skill. Do not auto-send DMs from GHL, Luke sends them
from his own account so they don't trigger spam filters.

### 2. Notion Page Write (via `Notion:create-page` skill)

Create one Notion page under the user's "Influencer Campaigns" parent
(or under `~/Vault/Projects/` if no Notion parent specified):

```
Title: Influencer Campaign, <Brand>, <YYYY-MM-DD>

Body structure:
- Header: Campaign brief (link to 00-brief.md)
- Toggle per tier (Macro / Micro / Nano)
  - One sub-toggle per handle containing:
    - DM text (copy-paste ready)
    - Brief (full)
    - Content angle (from table)
    - GHL contact link
- Kill list (read-only reference)
- Status tracker:
  - DMs sent: 0 / N
  - Replies: 0 / N
  - Confirmed yeses: 0 / N
  - Content posted: 0 / N
```

### 3. Surface to User

After both handoffs, output a one-screen summary:

```
Stage 6 complete.

Output: ~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/06-influencer-army.md

Handles written to GHL: <N> contacts tagged
  → tag: campaign-<brand-slug>-<date>
  → GHL search URL: <generated>

Notion page created: <URL>
  → Open to copy + send DMs

Next: Run Stage 7 (aggregate Higgsfield prompts) or send the first batch
of DMs from Notion.
```

## Selr AI Specifics

For Selr workshop campaigns, the canonical creator pool:

**Macro tier, usually skipped for Selr.** AU AI macros are mostly
US-pitched and too expensive for a 12-seat workshop. Skip and explain why.

**Micro tier, AU operator creators:**
- @kingstondental (operator-creator angle)
- AU founder-creators in trades / hospitality / professional services
- AU LinkedIn-leading SMB voices (10K-50K followers)
- AU YouTube channels for SMB ops + bookkeeping + tax (3K-25K subs)

**Nano tier, Skool members + workshop alumni:**
- Pull from Skool member directory (200+ members)
- Cross-reference with workshop attendee list (1,200+ alumni)
- Prioritise members who've shipped a Selr install and posted about it
- These are the highest-credibility carriers because they're operators
  recommending operator-to-operator

For Selr ASA campaigns, swap nano pool to:
- AU operator-founders who've completed an ASA install
- AU executive coaches with mid-market SMB rosters
- AU bookkeeping firms with SMB client networks

For non-Selr brands, derive the creator pool from the Stage 0 brief +
Stage 1 segment surfaces.

## Demo Output (Selr AI Melbourne Workshop)

```markdown
# Influencer Army: Selr AI Melbourne Workshop, 2026-05-24

## Tier: Macro

**Definition for this campaign:** 500K+ followers, 1-2 posts/week.

**Why we're skipping it:** AU AI macros are over-priced for a 12-seat
workshop ROI; audience overlap with our existing channels is low; macro
endorsements don't convert workshop seats, operator-to-operator
credibility does.

## Tier: Micro

**Definition for this campaign:** 25K-250K followers, 3-7 posts/week,
AU operator-creator focus.

| Handle | Platform | Niche fit (1-10) | Why they fit | Content angle for THIS brand | Risk flags |
|--------|----------|------------------|--------------|------------------------------|------------|
| @<aufounder1> | LinkedIn | 9 | AU SMB founder, 35K LinkedIn followers, posts daily on ops + scaling | "Walks through the 3 things he'd install in his own business if he attended the next Selr workshop, recorded as a vertical text post + 4:5 photo" | None known |
| @<auops2> | IG | 8 | Trades ops creator, 42K IG followers, AU East Coast | "Documents the 'before/after' of installing one AI workflow in his trades business, 30s Reel, 7 days apart" | Anti-corporate tone, keep DM AU-direct |
| @<aubuilder3> | X | 9 | Build-in-public founder, 80K X followers, indie agency space | "Thread of the 3 things he'd install in his own consultancy from the workshop curriculum, 8-12 tweets" | Recent sponsor with competing AI course, wait 30 days |
| @<auyt4> | YouTube | 8 | AU SMB ops creator, 18K subs, 15-min how-to format | "10-min video walking through the workshop curriculum from his perspective as an attendee" | None |
| @<aulinkedin5> | LinkedIn | 9 | AU operator coach, 60K LinkedIn followers | "Single text post recapping his read of the workshop format vs traditional AI courses" | None |

## Tier: Nano

**Definition for this campaign:** 1K-25K followers, Selr alumni +
Skool member focus, daily-plus posters.

| Handle | Platform | Niche fit (1-10) | Why they fit | Content angle for THIS brand | Risk flags |
|--------|----------|------------------|--------------|------------------------------|------------|
| @<alumni1> | IG | 10 | Brisbane workshop alumni, shipped a GHL install in March 2026 | "Posts a 30-day check-in Reel showing the install still running, tags @selr__ai" | None |
| @<alumni2> | LinkedIn | 10 | Sydney workshop alumni, runs a hospitality group | "LinkedIn essay on what the workshop changed about how she hires" | None |
| @<skool1> | IG + Skool | 9 | Active Skool member, posts 3x/week | "Reel showing his weekly Builder Call wrap-up, mentions Melbourne workshop" | None |
| @<skool2> | X | 9 | Active Skool member, indie founder | "Thread: 'I went to the Brisbane workshop. Here's what shipped', 8 tweets" | None |
| @<alumni3> | LinkedIn | 9 | Melbourne local, regional services | "Local-Melbourne text post, 'A workshop landing in our city next week, here's why I went last time'" | None |
| @<alumni4> | IG | 9 | Gold Coast local | "Reel of her Brisbane workshop day, re-shared with Melbourne city tag" | None |
| @<skool3> | LinkedIn | 8 | Skool member, AU SMB ops | "Carousel, what he installed at his workshop" | None |
| @<alumni5> | TikTok | 9 | Melbourne local, hospitality | "30s TikTok of her workshop day, voiceover only" | None |
| @<skool4> | YouTube | 8 | Skool member, weekly ops vlog | "Mentions Melbourne workshop in his upcoming weekly vlog" | None |
| @<alumni6> | LinkedIn | 10 | Melbourne local, services business | "LinkedIn text post, 'Why I'm going back to the next Selr workshop'" | None |

(... DMs and briefs follow ...)

## Kill List

- **@<aubigfounder1>**, Anti-AI public stance in February 2026 LinkedIn
  thread; audience would push back on partnership.
- **@<aumarketer2>**, Recent sponsor stack includes 3 competing AI
  courses; audience saturation.
- **@<aubigcoach3>**, Engagement rate 0.9% on 120K followers ,
  bought-follower signal.
```

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/06-influencer-army.md
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| DMs sound templated ("Hi [name]") | Re-write with a specific reference to recent work for each handle |
| Niche fit scores all 9-10 | Be more honest. Distribution should be 7-10 |
| No risk flags listed | Re-check, every creator has at least one flag (engagement rate, sponsor stack, voice mismatch) |
| Compensation framework says "TBD" | Pick one, product-only / fee+product / fee+commission |
| Kill list is empty | Add 2-4 cuts, you stopped thinking too early |
| GHL write fails | Surface to user, check `ghl-crm` auth, do not silently skip |
| Notion write fails | Surface to user, check Notion auth, do not silently skip |
| Auto-sent DMs | NEVER. Sister rule to "show Luke before any blast". DMs go to Notion for manual send |

## Next Stage

Once `06-influencer-army.md` is saved + voice-gated + handoffs executed,
Stage 7 aggregates every Higgsfield prompt from Stages 5+6 into the
paste-ready file.
