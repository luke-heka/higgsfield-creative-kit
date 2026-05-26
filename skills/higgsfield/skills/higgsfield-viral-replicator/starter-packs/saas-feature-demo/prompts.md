# SaaS Feature Demo: Ready-to-Use Prompts

> Three prompts. Run them in order. Each assumes the variables from
> `brief.md` are filled.

---

## Prompt 1: Deconstruct the viral reference (Path A Step 2)

```
You are running Step 2 of higgsfield-viral-replicator Path A for a
SaaS founder / indie hacker / micro-SaaS launch.

Read raw-post.json in the current output folder. Produce a 9-section
deconstruction using the exact schema in
~/.claude/skills/higgsfield/skills/higgsfield-viral-replicator/templates/deconstruction.md.

Fill EVERY field. Special attention for SaaS demos:
- §1 Hook archetype: pick from claim-then-prove, contrarian,
  demo-first, authority, visual-mismatch. SaaS winners cluster on
  demo-first (Marc Lou) and authority/receipt (Pieter Levels).
- §2 Pattern interrupts: SaaS demo reels have a specific cadence,
  0:00 to 0:03 hook (founder face or product still), 0:03 to 0:10
  demo with rapid click cuts, 0:10 to 0:20 result reveal (the aha),
  0:20 plus CTA. Map the reference to this cadence and note any
  deviation.
- §3 Narrative arc: the viewer's internal shift is "wait, that took
  how many clicks?" or "wait, this replaces my whole stack?". Name
  the specific moment the aha lands.
- §4 Visual style: name the surface (full-screen app demo, screen
  recording with webcam PIP, founder selfie with laptop visible,
  side-by-side incumbent-vs-ours). Name the typography of any
  on-screen text (font family feel, weight, contrast).
- §5 Audio role: SaaS demos almost always have NO music. Founder
  voice narrates the click flow. If the reference uses music, flag
  it as a deviation and note the energy curve.
- §6 Payoff: the payoff is the result-reveal moment, when the
  finished page / app / output appears on screen. Name the exact
  timestamp and the visual that lands.
- §7 CTA: SaaS demos use "try it at [URL]" or "the [PRICE_POINT]
  one-time deal at [URL]". NEVER "DM me", NEVER "comment INTERESTED".
  Tag the CTA verbatim.
- §8 Why it went viral: SaaS demos almost always trigger
  curiosity-gap-resolution ("the aha closed the gap") plus
  identity-confirmation ("the viewer sees themselves as the kind of
  builder who would use this"). Name which mechanic dominates.

Write the output to deconstruction.md. Voice-grade through
content-engine and humanizer.
```

---

## Prompt 2: Rebuild for the brand (Path A Step 4, Skeleton 4)

```
You are running Step 4 of higgsfield-viral-replicator Path A. Rebuild
the deconstructed reel for {{BRAND_NAME}}, a SaaS / micro-SaaS launch.

Brand context: paste the "Brand context block" from brief.md.

Use templates/rebuild-prompt-skeleton.md (Skeleton 4) as the canonical
structure. Produce three deliverables:

1. Shot-by-shot rebuild table in rebuild.md
   - Beat number, duration (sec), shot description, on-screen text
     (typed verbatim), audio, "what mechanic we are keeping"
   - 4 to 6 beats for a 20 to 30 second demo reel
   - Mark which beats are SCREEN RECORDING (real Loom/QuickTime
     capture, not Higgsfield) and which are HIGGSFIELD HERO SHOTS
     (cold open, founder at desk, product close-up)
   - SaaS demos typically have 1 Higgsfield hero shot at the cold
     open and 1 at the CTA close, with the middle 70% being live
     screen recording

2. Paste-ready Higgsfield prompt for the COLD OPEN hero shot in
   higgsfield.md
   - Use Skeleton 4 format
   - SaaS-specific fills:
     - DURATION: 3 to 5 seconds, 9:16 vertical (cold open only,
       short by design)
     - SUBJECT + ACTION: ONE action only. "Founder sits at single
       monitor and opens laptop lid" not "sits down AND opens laptop
       AND starts typing"
     - SETTING: home office with single monitor, coffee shop window
       seat, clean desk with one notebook. NEVER a stock-photo
       "team meeting" set, NEVER a server room, NEVER a corporate
       boardroom.
     - LIGHTING: "natural daylight from window screen-left, no key
       light, slight shadow on screen-right" (indie aesthetic, not
       cinema)
     - CAMERA: "static lock-off mid-shot" or "slow handheld push-in
       covering 4 inches over the duration" (same pattern as reference)
     - COLOR PALETTE: 3 anchors max from brand block. SaaS default:
       cool greys, single accent colour from the product, soft warm
       skin tones
     - AUDIO INTENT: "ambient room tone and keyboard sounds, no music"
     - BRAND VISIBILITY: "laptop screen shows the product UI in
       silhouette, no logo bug overlay" (the screen recording will
       carry the brand visibility in the middle beats)
     - EXCLUDE: universal anti-slop block PLUS
       "stock-photo team meeting, fake whiteboard with synergy
       diagrams, corporate enterprise lighting, suited founders,
       multiple monitors arranged for cinematic look, screen-glow
       fake reflections"

3. Caption draft in rebuild.md
   - ≤200 chars before the cutoff, then 1 to 2 sentence expansion
   - Founder voice from brand block. Honest, dry, slightly nerdy.
   - Soft CTA. Use "the {{PRICE_POINT}} link at [URL]" or
     "free trial if you want to try it on a real project". NEVER
     "DM me", NEVER vague "AI-powered" language.

Rebuild rules:
- KEEP from original: hook archetype, cadence (cold open + demo +
  result + CTA), result-reveal moment, founder-face placement
- CHANGE from original: subject, exact words, the demo content,
  on-screen text, the incumbent named
- One mechanic per rebuild. If the reference stacked demo-first +
  receipt + replace-incumbent, pick the one we can actually back up
  (do we have a real Stripe receipt? a real user count? a real diff
  vs the incumbent?)
- Resist on-the-nose. If the reference was Marc Lou scaffolding an
  app in ShipFast, don't rebuild as "{{BRAND_NAME}} scaffolds an app
  in 30 seconds". Translate the mechanic to {{BRAND_NAME}}'s actual
  hero benefit.

Voice-grade every text output through content-engine + humanizer
before saving.
```

---

## Prompt 3: Handoff dispatcher (Path A Step 6)

```
You are running Step 6 of higgsfield-viral-replicator Path A. Decide
which downstream reel skill assembles the full demo reel and write
the handoff note.

SaaS demo handoff selection rule:

| Rebuild visual style | Hand off to |
|---|---|
| Screen recording + on-screen text + named visual primitives (default SaaS demo) | motion-graphic-reels |
| Founder selfie + Stripe dashboard (Pieter Levels build-in-public style) | cinematic-ai-reels |
| Founder filming themselves narrating their own screen | frontcam-reels |
| Mixed (founder face + heavy on-screen text overlays) | cinematic-ai-reels + motion-graphic-reels overlay pass |

Fallback rule: if cinematic-ai-reels is not installed, route to
frontcam-reels and document the deviation in handoff.md.

Critical handoff note for ALL SaaS rebuilds: Higgsfield generates the
cold-open hero shot and optionally a CTA-close shot. The middle 70%
of the demo (the actual screen recording showing the product working)
MUST be captured live in Loom or QuickTime, NOT generated. The
handoff.md must include:
- A "live capture shot list" section listing every screen-recording
  beat from the rebuild table, with the exact clicks/actions to
  capture
- A note that the downstream reel skill stitches the Higgsfield
  hero shot + live screen recording + any motion-graphic overlays

Write handoff.md with:
- Which reel skill to load next
- Path to deconstruction.md
- Path to rebuild.md
- Path to higgsfield.md
- The live-capture shot list (the screen recording the founder
  needs to film themselves)
- Any SaaS-specific deviations (e.g. "needs a real Stripe screenshot
  inserted at beat 5, founder to capture")
- One-line summary suitable for ~/board/_log.md

Do NOT auto-invoke the downstream skill.
```
