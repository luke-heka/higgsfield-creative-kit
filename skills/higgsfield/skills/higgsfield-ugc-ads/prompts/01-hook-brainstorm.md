# Prompt 01: Hook brainstorm (Chat 1)

**Chat purpose:** Generate 5 hook variations for a UGC ad. ASK FIRST. Then write.

**Use in:** Chat 1 of the two-chat (three with critique) pattern. Keeps the
production chat clean by separating hook ideation from chunk-render context.

---

## The handoff message (paste this verbatim)

> Help me generate five hook variations for a UGC ad for my product `[URL]`.
>
> Before you write anything, ask me clarifying questions on:
>
> - Tone (founder voice / influencer voice / customer voice / authority)
> - The current ad I'm replacing (if any) so we don't repeat its angle
> - Angles I've ruled out
> - Target ICP (one line)
> - Whether I want the product mentioned by name in the hook or held for chunk 3
>
> Then write 5 hooks. Each hook must:
>
> - Be ≤12 words
> - Be sayable on camera in under 3 seconds
> - Stand alone as a Chunk 1 voiceover line with no setup
> - Come from a DIFFERENT archetype than the other 4 (pain, curiosity,
>   contrarian, proof/numbers, authority)
> - Match Selr AI house style (no em dashes, no banned vocab, see SKILL.md
>   "Style constraints")
>
> Format as a numbered list with the archetype label in brackets.
>
> End with a "REJECTED" footer listing 3 hooks you considered but cut, one
> line each on why (too generic, too on-the-nose, too jargony, etc.).

---

## What the model should ask back (checklist)

A good Chat 1 response opens with 4–6 questions, not 5 hooks. If the model
jumps straight to hooks without asking, abort and re-paste with: "Ask the
questions first. Do not write hooks until I've answered."

Questions the model SHOULD ask:

1. What tone fits, founder, influencer, customer, authority?
2. Is there a current ad I'm replacing? If yes, what's its angle so we don't
   repeat it?
3. Which angles are ruled out (e.g. fear-based, comparison-to-competitor)?
4. One-line ICP, who's watching this ad?
5. Should the product be NAMED in the hook (riskier, more specific) or held
   back until Chunk 3 (safer, higher curiosity)?
6. Any unique mechanism / ingredient / feature that's the product's "thing"?

---

## Output shape (what Chat 1 should return)

```
HOOK VARIATIONS

1. [archetype: PAIN]
   Your hook line here, ≤12 words.

2. [archetype: CURIOSITY]
   Your hook line here.

3. [archetype: CONTRARIAN]
   Your hook line here.

4. [archetype: PROOF / NUMBERS]
   Your hook line here.

5. [archetype: AUTHORITY]
   Your hook line here.

REJECTED (considered but cut)

- "[hook]", too generic, reads like every dropshipping ad
- "[hook]", banned vocab ("game-changer")
- "[hook]", needs setup, doesn't stand alone as Chunk 1
```

---

## Picking the chosen hook

After Chat 1 returns the 5, pick ONE based on:

| Criterion | Weight |
|-----------|--------|
| Matches the framework (mid-funnel = problem-aware; full-stack = cold) | High |
| Doesn't repeat the current ad's angle | High |
| Stops the scroll on its own (read it cold, would you keep watching?) | High |
| Sayable naturally on camera (no tongue-twisters) | Medium |
| Aligns with character voice (founder vs influencer) | Medium |

If none of the 5 land, browse `../shared/hook-bank-100.md` for an archetype
that wasn't generated. Common reason for "none land": the model defaulted to
pain + curiosity and missed contrarian / authority.

---

## Hand off to Chat 2

Pass the chosen hook line into Chat 2 (`prompts/02-multi-chunk-script.md`) as
`chunks[0].voiceover`. The rest of the chunks build around it.

---

## Voice gate (mandatory before locking the hook)

Run the chosen hook through `content-engine` first. If it flags em dashes,
banned vocab, or outcome promises, rewrite, don't lock a hook that fails the
ship-gate. The earlier you catch voice issues, the less per-chunk rework.

---

## Failure modes

| Failure | Cause | Fix |
|---------|-------|-----|
| All 5 hooks sound the same | Model didn't actually use 5 archetypes | Re-paste: "Use 5 DIFFERENT archetypes, pain, curiosity, contrarian, proof, authority. Do not repeat." |
| Hooks are too long | Model ignored ≤12 words | Re-paste with explicit "MAX 12 WORDS" and reject any longer in the response. |
| Every hook uses banned vocab | Model didn't load Selr AI style | Re-paste with the banned vocab list inline. |
| Hooks read as generic dropshipping ads | Model didn't use the product specifics | Re-paste with product URL + 3 specific product mechanisms inline. |
