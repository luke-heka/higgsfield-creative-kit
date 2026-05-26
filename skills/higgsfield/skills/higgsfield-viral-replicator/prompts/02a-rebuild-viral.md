# Prompt 02a, Rebuild the Viral Video for the User's Brand

You have:

- A 9-section deconstruction (from prompt 01a, written to
  `deconstruction.md`)
- A one-line brand + topic from the user (if not supplied, ask once)
- Any constraints the user named (length, platform, brand-mark visibility,
  founder-on-camera or not)

## Your job

Produce a REBUILD, a video that uses the original's STRUCTURE and
MECHANICS, but NOT its surface-level content or voice.

The output is two artefacts:

1. A shot-by-shot script (table format)
2. A paste-ready Higgsfield video prompt for the DOMINANT shot only

Both go into `rebuild.md` and `higgsfield.md` respectively.

## Inputs you should already have

Pull these directly from the deconstruction file:

- **Hook archetype** (deconstruction §1)
- **Pattern interrupts cadence** (deconstruction §2, cuts per 10s)
- **Narrative arc** (deconstruction §3, internal-shift beats, not
  play-by-play)
- **Mechanic to keep** (deconstruction §8, the named mechanic)
- **What NOT to copy** (deconstruction §9, protect against on-the-nose)

And from the user:

- **Brand + topic in one sentence.** Example: "Selr AI workshop offer
  for solo PTs wanting to install one AI workflow before they leave."
- **Platform + duration** if specified. Default: IG Reel, 9:16, 8s.

If brand is Selr AI, auto-load defaults:

- Voice from `~/.claude/projects/-Users-luke/memory/selrai-business-model.md`
- URLs from `~/.claude/projects/-Users-luke/memory/brand-contact-urls.md`
- House rules (no em dashes, no outcome guarantees, no support promises,
  AU English) from `~/CLAUDE.md`

## Output schema

```
# Rebuild, <brand>: <topic>

**Original mechanic we're keeping:** (1 line, pulled from deconstruction §1 + §8)
**What we're explicitly NOT copying:** (1 line, pulled from deconstruction §9)
**Target platform + duration:** (e.g. IG Reel, 9:16, 8s total, Higgsfield renders the dominant 5-8s shot)
**Hook archetype:** (same as original, name it)

---

## Shot-by-shot script

| Shot | Time | Visual | Audio | On-screen text |
|---|---|---|---|---|
| 1 | 0:00-0:01.5 | (describe the visual, match the original's framing logic, change the surface) | (music? VO? ambient?, match the original's audio role) | (the on-screen text in the user's brand voice) |
| 2 | 0:01.5-0:03 | ... | ... | ... |
| ... | | | | |

**Cuts per 10s in rebuild:** (should match deconstruction §2 within ±1)
**Dominant shot for Higgsfield render:** (which row above, usually shot 1 or the payoff shot)

## Caption draft

(One paragraph, ≤200 chars before the visible cutoff, then expansion.
Match the user's brand voice, NOT the original creator's voice. NO em
dashes, NO outcome promises, NO banned vocab.)

## Higgsfield video prompt (paste-ready, dominant shot only)

See `higgsfield.md`, uses `../shared/higgsfield-prompt-skeletons.md`
Skeleton 4 template.

## Why this rebuild works for THIS brand

2-3 sentences explaining how the kept mechanic maps onto the user's
audience. If you can't write this confidently, the rebuild is off,
go back and pick a different mechanic from the deconstruction.
```

## Rebuild rules (HARD)

- **KEEP:** hook archetype, pattern-interrupt cadence (cuts per 10s),
  payoff shape, CTA mechanic, audio role
- **CHANGE:** subject, setting, voice, specific words, music
- **NEVER copy verbatim:** captions, on-screen lines, phrasings.
  Paraphrase the structure, write fresh language.
- **One mechanic per rebuild.** If the original stacked 3 mechanics
  (curiosity-gap + status-transfer + comment-bait), PICK ONE that
  maps cleanest to the user's brand and audience. Document the choice
  in "why this rebuild works".
- **Resist on-the-nose.** If the original was about a sushi chef and
  the user makes insulated cups, don't rebuild as "an insulated cup
  chef." Translate the mechanic to the brand's actual world.
- **Brand voice ≠ original creator voice.** If you removed every
  brand-specific word and the caption still sounded like the original
  creator, rewrite, it's too derivative.

## Length discipline

- ≤8 seconds for the Higgsfield render (the model's sweet spot)
- Full edit can be longer (15-30s for a finished Reel), the Higgsfield
  prompt is for the DOMINANT shot only
- Cut anything that doesn't earn its time. If shot 4 is "supporting,"
  it dies first. Better to have 4 strong shots than 6 mediocre ones.

## Sanity check before delivering

Read the rebuild caption out loud:

1. Does it sound like the brand or like the original creator? If
   creator → rewrite.
2. If you removed every brand-specific word, would the rebuild still
   make sense for the user's audience? If not → it's too generic.
3. Does it contain any banned vocab (game-changer, 10x, transform,
   level up, secret sauce, unlock, supercharge, crushing it)? If yes →
   rewrite.
4. Does it contain an em dash? If yes → swap for a comma or full stop.
5. Does it promise an outcome ("you will get X result") or ongoing
   support ("weekly Q&A", "office hours")? If yes → swap to process
   language.

If all 5 pass, ship to step 5 (voice ship-gate via content-engine +
humanizer).

## Output destination

- `<output-folder>/rebuild.md`
- `<output-folder>/higgsfield.md`

Then run prompt `03a-handoff-to-reel-skill.md`.
