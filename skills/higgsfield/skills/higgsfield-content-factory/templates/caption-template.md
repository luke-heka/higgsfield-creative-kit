# IG Caption Template

The IG caption is the highest-leverage ranking signal after slide 1.
Front-load the hook, mobile cutoff is 125 chars, hashtags at the bottom,
3-5 niche tags only.

This template is the canonical caption shape across the factory.

---

## Field-by-field skeleton

```
<HOOK, ≤125 chars, identical to slide 1 hook by default>

<BODY, 3 to 5 short lines, context that the carousel doesn't fit on
slides. Each line is 1 sentence max. No emojis unless the idea card
explicitly asks. No em dashes, comma or full stop.>

<CTA, single instruction. Matches slide 7 CTA.
If "Comment WORD" CTA, the trigger word goes here verbatim.
If soft CTA, "Follow @<handle> for more like this." is the default.>

<HASHTAG BLOCK, 3 to 5 niche hashtags, lowercase, no spaces.
Selr AI house rule: 3-5 niche tags only, NOT 8-15 generic tags.>
```

---

## Worked example

For the worked-example idea card in `idea-card.md`:

```
5 tools you can ditch when you start using Claude Code as your operator

Most of the SaaS stack you're paying for monthly is automation glue.
Claude Code is glue. So most of the stack can go.

Here are 5 specific replacements with the exact mechanic that replaces them.

Run the swap one at a time so you don't break your workflow.

Comment STACK to get the full breakdown.

#claudecode #aiagents #solofounder #automation
```

Char count of hook line: 81 (under 125 mobile cutoff ✅).
Hashtag count: 4 (within 3-5 range ✅).
No em dashes ✅. No banned vocab ✅.

---

## Field-by-field rules

### Hook (line 1)

- ≤125 characters (IG mobile cutoff, anything past this gets hidden
  behind "...more").
- By default = identical to slide 1 hook text from the idea card.
- If shortening for char limit, keep the verb. Drop modifiers first.

### Body (lines 3-7, separated by blank lines)

- 3 to 5 short lines max.
- Each line is 1 sentence. No paragraphs.
- Context the carousel slides can't fit (why this matters, when to do
  it, what's next).
- No emojis unless idea card flag explicitly true.
- No em dashes. Comma or full stop.

### CTA (penultimate line)

- ONE instruction. No stacks of CTAs ("comment X and DM me and follow
  and share").
- Forms allowed:
  - "Comment WORD to get X." (ManyChat trigger word goes here in CAPS)
  - "Follow @<handle> for more like this." (soft, no ManyChat)
  - "Save this for next time you <task>." (engagement-focused, no
    funnel)

- Forms BANNED (Selr AI rules):
  - "DM me for help" / "Reach out anytime" → no-support-promise rule
  - "Come say hi" / "Swing past the workshop" → no-drop-in rule
  - "Get the system installed for free" → no-outcome-guarantee rule
  - "Money back if you don't love it" → no-refund-promise rule
  - "Click the link in bio" → IG penalises this in 2026, use Comment
    WORD instead

### Hashtags (last line)

- 3 to 5 hashtags. NOT 8-15.
- All lowercase.
- All niche (industry-specific or capability-specific). NOT generic
  ("#instagood", "#business", "#entrepreneur").
- One single line, space-separated. No line breaks between tags.

---

## Total caption length

- Hard ceiling: 2,200 chars (IG limit). Hard-fail if over.
- Soft target: 800-1,400 chars (reads-best zone for educational
  carousels per 2026 IG data).
- If running long, trim body lines BEFORE trimming hook or CTA.

---

## Voice grade

Before saving caption.md, pipe the full caption through:

1. `content-engine`, voice + slop check
2. `humanizer`, AI-tell removal

If content-engine fails on banned vocab, fix and re-grade. Loop until
pass. Do NOT ship without both passes.

---

## Rejected (do not write captions this way)

- ❌ Caption opens with a question ("Have you ever wondered..."). IG
  algorithm deprioritises question-opens in 2026.
- ❌ Caption uses em dashes anywhere.
- ❌ Caption uses 10+ hashtags. The 3-5 rule is a Selr AI house rule
  derived from 2026 IG signal data, more hashtags lower reach.
- ❌ Caption stacks 3 CTAs ("comment X, DM me, follow"). One CTA
  only.
- ❌ Caption uses "transform", "10x", "game-changer", "secret",
  "unlock", "level up", or any other banned word.
- ❌ Caption hook restates the slide 1 hook differently. Keep them
  identical, algorithm reads both and rewards consistency.
- ❌ Caption ends with "🔥🔥🔥" or any emoji unless idea card flag
  set.

---

## See also

- `idea-card.md`, the schema this caption draws from
- Selr AI house rules: `~/CLAUDE.md` "Style constraints"
- `~/.claude/skills/content-engine/`, voice grade ship gate
- `~/.claude/skills/humanizer/`, AI-tell removal
