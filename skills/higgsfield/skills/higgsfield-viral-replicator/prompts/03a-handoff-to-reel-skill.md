# Prompt 03a, Hand Off to the Right Reel Assembly Skill

You've produced either:

- A rebuild (Path A, `rebuild.md` + `higgsfield.md` for the dominant shot)
- A testimonial treatment (Path B, `treatment.md` + `higgsfield.md`)

This skill does NOT assemble the final reel. Assembly is the job of
either `cinematic-ai-reels` or `motion-graphic-reels`, depending on the
character of the source material.

Your job here: pick the right hand-off target and write `handoff.md`.

## Dispatcher rule for Path A (viral rebuild)

Read the deconstruction's §4 (Visual style) and §5 (Audio role). Match
against this table:

| Visual + audio character | Hand off to |
|---|---|
| Talking-head with cuts + warm grade + voice carries the spot (Kallaway, Hormozi, Iman Gadzhi, Justin Welsh) | **`cinematic-ai-reels`** (real VO + AI B-roll mix is the cinematic stack's specialty) |
| 100% motion-graphic with typeset text + named visual primitives (Greg Isenberg, Jay Clouse, Daniel Stojnic) | **`motion-graphic-reels`** (Greg-style with locked Selr palette + Fraunces type) |
| Mixed (real talking-head + motion-graphic overlays, common for explainer reels) | **`cinematic-ai-reels`** as primary, with `motion-graphic-reels` primitives layered in post |
| Pure UGC product unboxing / user-generated / "this is my actual desk" | Pre-empt and STOP, this should route to `higgsfield-ugc-ads`, not the reel skills. Write `handoff.md` flagging the wrong route. |
| Pure AI-generated cinematic narrative (no real footage, all model-generated) | **`cinematic-ai-reels`** (it's the cinematic-stack home) |

If `cinematic-ai-reels` isn't installed yet (check
`~/.claude/skills/cinematic-ai-reels/`), fall back to
`motion-graphic-reels` and note the deviation in `handoff.md`.

## Dispatcher rule for Path B (testimonial treatment)

Read the chosen treatment from `treatment.md`. Match against this table:

| Treatment | Hand off to | Why |
|---|---|---|
| **A, Talking-head reconstruction** | `cinematic-ai-reels` | AI talking head needs the cinematic stack's grade + audio polish to read as a real customer |
| **B, Text-on-b-roll with VO** | `motion-graphic-reels` | Text-on-screen typography is the motion-graphic primitive's job |
| **C, Side-by-side before/after** | `motion-graphic-reels` | Split-screen + label primitives are motion-graphic territory |

## handoff.md schema

```
# Hand-off, <source-slug>

**From:** higgsfield-viral-replicator
**To:** <cinematic-ai-reels | motion-graphic-reels>
**Path:** <A, viral rebuild | B, testimonial treatment>
**Date:** <YYYY-MM-DD>

## Source files (paths)

- Source material: `<raw-post.json | raw-reviews.json>`
- Structural analysis: `<deconstruction.md | themes.md>`
- Rebuild / treatment: `<rebuild.md | treatment.md>`
- Higgsfield dominant-shot prompt: `<higgsfield.md>`

## What the receiving skill needs to do

1. (e.g. for cinematic-ai-reels) Load the Higgsfield prompt as the
   dominant shot. Generate 3-5 supporting B-roll chunks using the
   visual style notes from deconstruction §4. Assemble under the VO
   script from rebuild.md.
2. (e.g. for motion-graphic-reels) Use the deconstruction §3 narrative
   arc as the 7-beat structure. Map each beat to a named visual
   primitive from `motion-graphic-reels/references/motion-vocabulary.md`.
   Render with Selr palette + Fraunces type.

## Deviations from the receiving skill's default flow

(List any, e.g. "Cuts/10s in original was 6, default for cinematic-ai-reels
is 3-4, increase cut frequency in assembly" or "Original has no VO,
use ambient + cuts as rhythm, skip VO generation step.")

## Voice ship-gate status

- content-engine: <PASS | FAIL, list failing lines>
- humanizer: <PASS | FAIL, list failing lines>

The receiving skill MUST re-run content-engine + humanizer on any new
text it generates (captions, on-screen text, VO lines). The gate from
this skill only covers the rebuild/treatment script.

## Disclosure requirements (Path B only)

If treatment A (talking-head reconstruction):
- ON-SCREEN TEXT REQUIRED: "Represents a customer profile, not a specific person"
- Bottom-corner placement, full duration of talking-head shot
- Non-negotiable for ad-platform compliance

## CTA + end-card

The receiving skill is responsible for the end-card. If brand is Selr AI,
auto-wire through `community-publishing-pipeline` (GitHub → Notion →
ManyChat) for the CTA destination. Otherwise the receiving skill asks
the user for the CTA target.

## Next command for the user

To proceed, the user should run:

> "now run <cinematic-ai-reels | motion-graphic-reels> on the hand-off at <output-folder>"

This skill does NOT auto-fire the downstream skill. The hand-off is a
deliberate boundary, the user inspects the rebuild/treatment before
committing to the render+assembly pipeline.
```

## Output destination

Write to: `<output-folder>/handoff.md`

Then append a one-line entry to `~/board/_log.md`:

```
- viral-replicator: <Path A deconstructed @<handle> <post-id>, rebuilt for <brand>> | <Path B clustered <N> reviews into <M> themes for <brand>> (handoff → <reel-skill>) (<YYYY-MM-DD>)
```
