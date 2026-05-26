# Idea Card Template

One idea card = one carousel slot. The card is the minimum viable unit
that Stage 3 (Generate) can consume without re-deciding anything.

Stage 2 (Plan) produces ~40 of these, one per row of the 60-day calendar.

---

## Field-by-field schema

```yaml
slot_number:           # integer, 1-indexed across the run
post_date:             # YYYY-MM-DD
post_day:              # Mon | Tue | Wed | Thu | Fri | Sat | Sun
post_time:             # HH:MM AEST (default 06:00)
batch_number:          # integer, which Stage 3 batch this card belongs to

# Content
hook:                  # ≤125 char (IG mobile cutoff). Slide 1 text. Voice-graded.
hook_archetype:        # one of hook-bank-100 archetype names
                       # (Problem-Aware | Contrarian | Curiosity-Gap |
                       # Authority | Pattern-Interrupt | Specific-Number | etc.)
template:              # one of the 15 carousel-* template names
slide_purpose:         # one of: tips | cheat-sheet | stack-reveal | case-study |
                       # myth-bust | mistakes | feature-update | feature-spotlight |
                       # skill-announce | skill-card | metaphor-explainer |
                       # prompt-anatomy | replace-this | reel-cover

body:
  - slide: 2
    text:              # the actual body text for slide 2
  - slide: 3
    text:              # slide 3
  - slide: 4
    text:              # slide 4
  - slide: 5
    text:              # slide 5
  - slide: 6
    text:              # slide 6 (if template uses it)

cta:                   # slide 7 text. One instruction. Voice-graded.
cta_word:              # if "Comment WORD" CTA, the trigger word for ManyChat
                       # (otherwise null)

# Supporting imagery (Higgsfield only)
higgsfield_image:      # true | false (default false)
higgsfield_image_slide: # 4 | 7 (which slide the image lands on, if true)
higgsfield_image_prompt: # full Skeleton 3 prompt (only if higgsfield_image: true)
higgsfield_model:      # nano-banana | gpt-image-2 | soul (only if higgsfield_image: true)

# Caption
caption_hook:          # ≤125 char (matches slide 1 hook by default)
caption_body:          # 3-5 lines of context
caption_cta:           # matches slide 7
caption_hashtags:      # array of 3-5 niche hashtags (NOT 8-15 generic)

# Voice grade record
content_engine_pass:   # true | false (must be true before Stage 3 reads card)
humanizer_pass:        # true | false (must be true before Stage 3 reads card)
voice_grade_notes:     # any issues caught + fixes applied

# Source / provenance
source_research_rank:  # which of the Stage 1 top 20 this card derives from (1-20)
research_inspired_by:  # competitor handle + hook that inspired this card
```

---

## Worked example

```yaml
slot_number: 03
post_date: 2026-05-28
post_day: Wed
post_time: 06:00
batch_number: 1

hook: "5 tools you can ditch when you start using Claude Code as your operator"
hook_archetype: Specific-Number
template: carousel-stack-reveal
slide_purpose: stack-reveal

body:
  - slide: 2
    text: "Zapier, replaced by a 12-line bash script + cron"
  - slide: 3
    text: "Make.com, replaced by Claude Code agents running on a $5 VPS"
  - slide: 4
    text: "Buffer, replaced by omnisocials + a daily routine"
  - slide: 5
    text: "Calendly, replaced by a Claude Code routine that reads your calendar"
  - slide: 6
    text: "Notion AI, replaced by Claude Code with read access to the same DB"

cta: "Comment STACK to get the full breakdown of how each replacement works"
cta_word: STACK

higgsfield_image: true
higgsfield_image_slide: 4
higgsfield_image_prompt: |
  4:5 VERTICAL INSTAGRAM CAROUSEL SLIDE, supporting context for "Buffer
  replaced by omnisocials + a daily routine", visual concept: clean
  laptop screen showing a terminal window with cron schedule output,
  typography: none, image only (carousel-generator types the slide),
  layout: laptop centered slightly low in frame, color palette: #1A1A1A
  laptop bezel #FFFFFF desk #7B61FF subtle purple terminal text glow,
  texture: clean photographic no grain, imagery: laptop with terminal
  open showing readable cron output, mood: focused calm,
  brand cues: Selr AI purple accent via terminal text only no logo,
  EXCLUDE: stock photo people, gradient background, emoji, drop shadows,
  hashtag overlays, watermark, typography handled by carousel-generator,
  AI-glossy skin, plastic shine, hyper-saturated colors
higgsfield_model: nano-banana

caption_hook: "5 tools you can ditch when you start using Claude Code as your operator"
caption_body: |
  Most of the SaaS stack you're paying for monthly is automation glue.
  Claude Code is glue. So most of the stack can go.

  Here are 5 specific replacements with the exact mechanic that
  replaces them.

  Run the swap one at a time so you don't break your workflow.
caption_cta: "Comment STACK to get the full breakdown."
caption_hashtags:
  - "#claudecode"
  - "#aiagents"
  - "#solofounder"
  - "#automation"

content_engine_pass: true
humanizer_pass: true
voice_grade_notes: |
  - Stripped "game-changing" from line 2 of body
  - Replaced em dash with comma in caption_body
  - Removed "level up" from CTA

source_research_rank: 7
research_inspired_by: "@gregisenberg, 'The SaaS I cancelled this month' carousel"
```

---

## Rejected (do not write a card this way)

- ❌ Hooks like "Discover the game-changing way to..." → banned vocab,
  fails content-engine.
- ❌ Body slides that are sentences not punches. Each body slide is a
  punch. If a body slide reads as 2+ sentences without a hard verb,
  re-write tighter.
- ❌ "Comment for support" or "DM me for help" CTAs, break Selr AI no-
  support-promise rule.
- ❌ More than 5 hashtags. Selr AI house style: 3-5 niche tags only.
- ❌ Higgsfield image on every slide. Most carousels need 0 supporting
  images. Only flag the card when it genuinely needs one.
- ❌ Em dashes anywhere. Comma or full stop.
- ❌ Body slides longer than slide 4 of `carousel-cheat-sheet`'s max
  char count, check the template's SKILL.md.

---

## Kill criteria

- Hook > 125 chars → reject, re-write shorter.
- Any body slide that doesn't sit inside the chosen template's slot
  schema → reject, switch template OR shorten body.
- `content_engine_pass: false` after 3 attempts → STOP, hand card back
  to user for manual rewrite.
- `higgsfield_image_prompt` doesn't use Skeleton 3 from
  `../../shared/higgsfield-prompt-skeletons.md` → reject, fix prompt
  shape.

---

## See also

- `../../shared/hook-bank-100.md`, hook archetype reference
- `../../shared/higgsfield-prompt-skeletons.md`, Skeleton 3 for the
  optional supporting image
- `caption-template.md`, caption structure (paired with this card)
- `~/.claude/skills/carousel-<template>/SKILL.md`, per-template schema
  for the matching `carousel-template.json`
