# Prompt 04: Critique loop (Chat 3)

**Chat purpose:** Hand the assembled final cut to `higgsfield-ad-critic` for
frame-by-frame Gemini analysis. Apply suggestions. Loop until green-lit.

**Use in:** Chat 3 of the three-chat pattern. Fresh context. Never reuse
Chat 1 or Chat 2, the critique conversation generates a lot of
back-and-forth that would blow the production context.

---

## The handoff message (paste this verbatim)

> Critique this UGC ad frame-by-frame and give me honest, specific feedback
> on how to improve it before I ship.
>
> Final cut: `~/board/_active/ugc-ads-<date>/03-final-1080p.mp4`
> Per-chunk source files: `~/board/_active/ugc-ads-<date>/chunks/chunk-{N}.mp4`
> Multi-chunk YAML: `~/board/_active/ugc-ads-<date>/02-script.yaml`
>
> Use the `higgsfield-ad-critic` sibling skill. Score on:
>
> 1. **Hook strength**, does the first 3 seconds stop scroll?
> 2. **Product visibility timing**, does the product appear when the script
>    says it should (Chunk 3 for mid-funnel)?
> 3. **Character consistency**, is the presenter the same person across
>    every chunk? Note any drift in face shape, hair colour, wardrobe.
> 4. **Voice consistency**, same voice across all chunks?
> 5. **Pacing**, any chunk feel rushed or dragging?
> 6. **AI-look tells**, uncanny mouth movement, eye drift, hand artifacts,
>    background morphing, perfect skin, studio lighting in a "kitchen"
>    setting.
> 7. **CTA clarity**, can a cold viewer tell exactly what to do after the
>    ad ends?
> 8. **Voice ban-list compliance**, any banned vocab, em dashes, outcome
>    guarantees, support promises, drop-in invites?
>
> For each issue found, suggest the cheapest fix:
>
> - **CapCut fix** (free, recommended), speed adjustment, B-roll overlay,
>   caption tweak, music level
> - **Single-chunk regenerate** (~5-8 credits), only if the chunk is the
>   issue
> - **Script rewrite** (Chat 2 round-trip), only if the voiceover or
>   structure is the issue
>
> NEVER suggest a full-ad regenerate. That's a refactor, not a fix.

---

## What Chat 3 returns (output shape)

The critic produces a structured report:

```
CRITIQUE REPORT, ugc-ad-<date>, v{iteration}

SCORE
- Hook strength: [1-10], [one-line reason]
- Product visibility timing: [PASS / FAIL], [reason]
- Character consistency: [PASS / FAIL with chunk numbers]
- Voice consistency: [PASS / FAIL with chunk numbers]
- Pacing: [PASS / FAIL with chunk numbers]
- AI-look tells: [list any spotted, with timestamps]
- CTA clarity: [PASS / FAIL], [reason]
- Voice ban-list compliance: [PASS / FAIL with specific lines]

ISSUES (sorted by severity)

1. [Severity: HIGH/MED/LOW] [Chunk N | Whole ad]
   What: [description]
   Why it matters: [reason]
   Fix: [CapCut fix | Single-chunk regenerate | Script rewrite]
   Specific instruction: [exact action to take]

2. ...

GREEN-LIGHT or NOT-YET
- GREEN-LIGHT: ship after applying any LOW-severity fixes
- NOT-YET: at least one HIGH-severity issue needs resolving; re-loop
```

---

## Applying critique suggestions

For each issue, work in cheapest-fix-first order:

### CapCut fix (always try first)

| Critic finding | CapCut fix |
|---------------|-----------|
| Chunk N pacing rushed | Speed adjust to 80-90% on that chunk |
| Chunk N hallucination (head enlarges, hand artifact) | B-roll overlay from adjacent chunk + mute audio for that section |
| Caption misread voiceover | Re-do auto-caption with manual correction |
| Music too loud over voice | Music level to -18 LUFS under voice |
| Cut between Chunk N and N+1 feels long | Tighten, gap should be ≤0.3s |
| CTA cut off | Extend final chunk's last frame as a 0.5s freeze + add CTA overlay text |

### Single-chunk regenerate (only if CapCut can't fix)

When to regenerate a single chunk:

- Chunk's character doesn't match the others (Soul ID drift)
- Chunk's product doesn't match (Element tag drift)
- Chunk's voiceover line is wrong (audio re-render needed)
- Chunk's framing exposes too much/too little of the product

Do NOT regenerate for:

- Short hallucinations (use CapCut overlay)
- Voice mismatch (use Change Voice)
- "Just feels off" (define what's off first, then regenerate with a
  specific fix)

### Script rewrite (Chat 2 round-trip, last resort)

Only when:

- The chunk role is wrong (e.g. needs to be agitation, not solution)
- The voiceover line is fundamentally flawed (multiple critic passes
  flagged the same line)
- The framework is wrong (mid-funnel needs to be full-stack or vice versa)

Going back to Chat 2 wastes the chunks already rendered. Only do this if
the cheaper fixes won't resolve a HIGH-severity issue.

---

## The critique-revise loop

```
Iteration 1:
  1. Send 03-final-1080p.mp4 to higgsfield-ad-critic
  2. Receive 04-critique-v1.md
  3. Apply ALL HIGH-severity fixes
  4. Apply MED-severity fixes if cheap
  5. Re-export → 03-final-1080p.mp4 (overwrites)

Iteration 2:
  6. Re-send to higgsfield-ad-critic
  7. Receive 04-critique-v2.md
  8. If GREEN-LIGHT → move to ship-gate (Phase 8)
  9. If NOT-YET → repeat

Cap: 3 iterations. If still not green after 3, the ad is fundamentally
broken, go back to Chat 2 and rewrite the script.
```

Save each iteration's critique to
`~/board/_active/ugc-ads-<date>/04-critique-v{N}.md`. Future-you (or another
agent) will read the loop history to learn what the critic flagged.

---

## What "green-light" means

Green-light from the critic does NOT mean ship. It means "no HIGH-severity
issues remain". The ship gate is still Phase 8, `content-engine` + `humanizer`
on the caption + on-screen text. Critic checks the VIDEO; ship-gate checks
the TEXT.

Both must pass before the ad goes live.

---

## Failure modes

| Failure | Cause | Fix |
|---------|-------|-----|
| Critic says "looks great" with no issues | Critic over-indexed on AI-positivity | Re-prompt: "Be ruthlessly specific. Name 3 things you would change. No 'looks great' summary." |
| Critic suggests full-ad regenerate | Critic ignored cheap-fix priority | Re-prompt with the cheap-fix-first table inline |
| Critic flags hook as weak after 2 iterations | Hook was wrong from Chat 1 | Go back to Chat 1, pick a different hook from the 5, re-render Chunk 1 only |
| Critic flags voice ban-list violations not caught in Chat 2 | content-engine wasn't run on the voiceover lines | Run content-engine NOW on every voiceover. Fix violations. Regenerate affected chunks. |
| Loop has run 3 times, still NOT-YET | Script structure is wrong | Chat 2 rewrite. Don't burn a 4th iteration. |

---

## Hand off to Phase 8

Once the critic gives GREEN-LIGHT, move to the ship-gate:

1. Run final caption + hashtags + on-screen text through `content-engine`.
2. Run the same text through `humanizer`.
3. Both pass → save to `05-ship-checklist.md` and ship.

The skill is done when `05-ship-checklist.md` is written and the final MP4
is posted (or queued for posting via `omnisocials` / `community-publishing-pipeline`).
