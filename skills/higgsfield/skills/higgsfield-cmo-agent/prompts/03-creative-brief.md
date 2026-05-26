# Stage 3: Creative Briefs

Read `01-segments.md` and `02-channel-plan.md`. Write ONE creative brief
per segment. These briefs drive every post in Stage 5 and every influencer
angle in Stage 6. Write them like the next person to read them is the
photographer or the video director.

## Per-Segment Brief Format

Use this exact structure for each segment:

```markdown
## Brief: Segment N: [name from Stage 1]

**Big idea (one sentence, no commas):**
The single thought every asset for this segment must communicate.
One sentence. No subordinate clauses. No commas. If you need a comma,
you have two ideas, cut to one.

**Insight we're leveraging:**
One paragraph. The customer truth that makes the big idea land. This is
the "why now" for this segment. NOT a stat. NOT a generic observation.
A specific, current, named truth about how this segment lives and
decides today.

**Message hierarchy:**
1. Lead with: [the headline thought, voice-graded]
2. Support with: [the proof that earns the lead]
3. Demonstrate by showing: [the visual or moment that anchors the proof]
4. Permission to believe: [the credibility marker, case, named client,
   data point, time-stamp, mechanism]

**Visual direction:**
- Setting: [named environment, not a vibe]
- Subject(s): [who's in frame + what they're doing]
- Lighting / time of day: [direction + quality]
- Camera energy: [still / handheld / drone / FPV, pick ONE]
- Color palette anchors: [3 colors max, hex if known]
- Texture cues: [film grain / matte / clean digital / etc.]
- Product visibility: [hero / incidental / off-frame, pick ONE per asset
  type]

**Voice/copy direction:**
- Tone words (3 max): [e.g. "direct, dry, competent"]
- Phrases to use: [3-5 phrases that anchor the voice]
- Phrases banned: [3-5 phrases that break it, Selr ban-list applies
  universally]

**Do (3-5 things creative MUST do):**
- [Specific, named direction]
- [Specific, named direction]
- ...

**Don't (3-5 things creative MUST NOT do):**
- [Specific anti-pattern]
- [Specific anti-pattern]
- ...

**Reference clues (NOT a moodboard, text descriptions only):**
- [2-3 directional references described by composition, not brand. E.g.
  "Single subject mid-frame with shoulders cut by lower-third, late-
  afternoon side light, single accent colour drawing the eye to the hand
  holding the laptop", NOT "shot like Apple ads"]
```

## Throughline Footer (Mandatory)

After all per-segment briefs, write **the throughline** in one paragraph:

```markdown
## The Throughline

One paragraph naming the connective tissue across all briefs. This is
what stops the campaign from looking like four different brands. It
names the SHARED CUSTOMER TRUTH, the SHARED VISUAL ANCHOR, and the
SHARED VOICE MARK. Three sentences max.
```

The throughline is the most important paragraph in this stage. If you
can't write a throughline that connects all 4 segments, your segments
are over-fragmented (re-check Stage 1) or your briefs are
over-personalised (re-check this stage).

## Rules

1. **Big idea is one sentence, no commas.** Force the constraint.
2. **Insight is a paragraph, not a stat.** "82% of SMBs use ChatGPT" is
   not an insight. "AU operators have started installing AI themselves
   between school pickups, not in dedicated learning blocks" is.
3. **Message hierarchy is 4 lines, no more.** If you can't hierarchise in
   4 lines, the message isn't clear.
4. **Visual direction names ONE camera energy per segment.** Picking 3
   ("handheld + drone + FPV") = no direction.
5. **Phrases banned is segment-specific PLUS the universal Selr ban-list.**
   Add ban entries that are specific to this segment (e.g. for a B2B SMB
   segment, ban "transform your business").
6. **Do/Don't is concrete.** "Be authentic" is not direction. "Show the
   founder typing on a beat-up laptop in real office light, not a styled
   setup" is.
7. **Reference clues describe composition, not brand.** Never "shot like
   Apple". Always "single subject left-third, negative space right, hard
   side-light from window, palette 80% earth tones".

## Skill Dependency: `content-marketer` (Strategic Phrasing)

For the **Big Idea** and **Insight we're leveraging** fields specifically,
call `content-marketer` skill to borrow the elite-strategist voice. Pipe
in the segment's Stage 1 + Stage 2 context, ask for the big idea sentence
and the insight paragraph, then run the result through the voice gate
(Selr ban-list applies) before locking in.

Do NOT outsource the whole brief to `content-marketer`, just the two
strategic fields. The rest is execution-craft and stays in this skill.

## Voice Gate (Mandatory Before Saving)

1. `content-engine`, strip slop, support promises, drop-in invites,
   outcome guarantees, personal life references, em dashes, AU/US
   English mismatch.
2. `humanizer`, strip signs-of-AI-writing patterns.
3. `content-marketer`'s output also gets graded, don't trust strategic
   phrasing past the gate just because it sounds expensive.

## Output File

```
~/board/_active/cmo-agent-<brand-slug>-<YYYY-MM-DD>/03-creative-briefs.md
```

## Failure Modes

| Symptom | Fix |
|---------|-----|
| Big idea has a comma | Rewrite. Constraint exists for a reason |
| Insight is a stat | Replace with a named, current customer truth |
| Message hierarchy is 8 bullets | Cut to 4. The hierarchy IS the constraint |
| Visual direction names "handheld + drone + tripod" | Pick ONE camera energy per asset type |
| Phrases-to-use field is empty | Force 3-5 phrases, voice can't be inferred from absence |
| Throughline says "all segments value quality" | That's not a throughline. Name the shared CUSTOMER truth + the shared VISUAL anchor + the shared VOICE mark |
| Brief reads like a moodboard | Strip brand references from reference clues, describe by composition only |
| `content-marketer` output uses "transform" or "elevate" | Re-grade through Selr ban-list. The elite voice still has to clear the gate |

## Selr AI Specifics

For Selr AI workshop briefs, the canonical voice anchors:

- **Phrases to use:** "in the room", "by 5pm", "you install it", "we
  walk through it together", "tested at the workshop", "your inbox
  triages itself", "operator-to-operator", "we share the same room".
- **Phrases banned (Selr-specific in addition to the universal ban-list):**
  "transform your business", "scale to 7 figures", "AI-powered",
  "next-level", "game-changer", "10x", "unlock", "elevate", "supercharge",
  "secret sauce", "hidden growth lever".
- **Voice anchors:** Confident, dry, AU-direct, treats the customer as
  competent.
- **Visual anchors:** Workshop room with operators around a table;
  Luke + Harvey on the wall side; real laptops, real notebooks, real
  coffee cups, AU power outlets visible; muted natural light through
  side windows; Selr purple appears ONCE per frame as accent, never
  background.

## Demo Output (Selr AI Melbourne Workshop, Segment 1)

```markdown
## Brief: Segment 1: AU SMB operators with a recurring ops bottleneck

**Big idea (one sentence, no commas):**
You install one working AI workflow in one room in one day and walk out
with it running.

**Insight we're leveraging:**
AU SMB operators between $1M and $10M revenue keep buying AI courses
and never finishing them. They have a recurring ops bottleneck that's
costing them a hire or a weekend, and they can name it inside 30
seconds. What they actually want is a deadline, a room, and someone in
the room who has installed this thing before. Not a curriculum. Not a
sequence. Not "complete the modules at your own pace."

**Message hierarchy:**
1. Lead with: The hands-on install workshop in your city.
2. Support with: 12 operators in the room, one workflow each, ships by
   5pm.
3. Demonstrate by showing: A founder closing their laptop and saying
   "okay, that's live."
4. Permission to believe: 1,200+ workshop attendees across Brisbane,
   Melbourne, Sydney; 200+ Skool members running their own installs;
   Harvey + Luke deliver every workshop in person.

**Visual direction:**
- Setting: A standard AU coworking workshop room, 12 chairs around 3
  trestle tables, projector, Luke + Harvey at the front. Real venue,
  not a styled set.
- Subject(s): One workshop attendee mid-install, laptop open, focused
  expression, not staged eye-contact with camera.
- Lighting / time of day: Mid-morning, side-lit through tall windows,
  natural overhead fluorescent fill switched off so the room feels human.
- Camera energy: Handheld with slight natural wobble. No tripod stills,
  no drone, no FPV.
- Color palette anchors: #1A1A1A (dark wood table), #F5F1E8 (cream walls),
  #7B61FF (Selr purple, accent only, single notebook spine in frame).
- Texture cues: Fine film grain, natural skin texture, no plastic AI
  shine.
- Product visibility: Incidental. Selr purple appears once per frame,
  never centred.

**Voice/copy direction:**
- Tone words: direct, dry, competent.
- Phrases to use: "in the room", "by 5pm", "you install it", "we walk
  through it together", "operator-to-operator".
- Phrases banned: "transform", "AI-powered", "next-level", "10x",
  "unlock", "scale", "guaranteed", "elevate", "supercharge", "game-
  changer", "secret sauce". (Plus universal Selr ban-list.)

**Do:**
- Show the actual workshop room with actual attendees mid-install.
- Show Luke or Harvey beside an attendee's laptop, not behind a podium.
- Show one workflow shipping in real time (terminal output, Slack ping,
  email send confirmation).
- Use Selr purple ONCE per frame as accent (notebook spine, single
  laptop sticker, lanyard).
- Caption every Reel with an operator-to-operator opener ("You don't
  need another AI course", "Stop watching tutorials. Install one
  thing.").

**Don't:**
- Stage a "thinking" pose at a clean white desk.
- Use stock AI-glow visuals (neon circuits, holographic interfaces).
- Show a stack of certificates or course completion screens.
- Use US-centric examples (CrossFit Austin, Silicon Valley founders).
- Use any "ongoing support" or "lifetime access" language.

**Reference clues:**
- A working classroom shot from a Saturday school basketball coaching
  clinic, multiple adults around tables, side-lit through gym windows,
  one coach beside a player's notebook. Not a TED talk staging.
- A trades course room, practical, real materials, real tools, no
  influencer-aesthetic styling.
- A small founder-led product launch event, 12 people, real venue,
  one big screen, founder talking from beside the audience not above
  it.
```

(... Segments 2, 3, 4 follow same format ...)

```markdown
## The Throughline

Every brief lands on the same shared truth, AU operators learn by
installing in a room with other operators, not by watching a course
alone. The shared visual anchor is the workshop room itself, captured
handheld with natural side-light and Selr purple as a single-frame
accent. The shared voice mark is operator-to-operator AU directness ,
no hype words, no outcome promises, no agency framing.
```

## Next Stage

Once `03-creative-briefs.md` is saved and voice-gated, Stage 4 reads it
plus 01-02 and writes the 4-week launch plan.
