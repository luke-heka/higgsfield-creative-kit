# Coach Hook Reel: Ready-to-Use Prompts

> Three prompts. Run them in order. Each assumes the variables from
> `brief.md` are filled.

---

## Prompt 1: Deconstruct the viral reference (Path A Step 2)

```
You are running Step 2 of higgsfield-viral-replicator Path A for an
online coach / course creator.

Read raw-post.json in the current output folder. Produce a 9-section
deconstruction using the exact schema in
~/.claude/skills/higgsfield/skills/higgsfield-viral-replicator/templates/deconstruction.md.

Fill EVERY field. Special attention for coach reels:
- §1 Hook archetype: pick from claim-then-prove, contrarian,
  specific-number, story-in-1-sentence, authority, problem-aware.
  Coach winners cluster on claim-then-prove and authority. If the
  reference uses a receipt (Stripe screenshot, client text-message,
  before-after revenue), mark it claim-then-prove + receipt-evidence.
- §2 Pattern interrupts: coach reels typically have 3 to 6 beats in
  30 seconds. If the reference is Greg-style motion-graphic, expect
  beats of 1.5 to 2.5 seconds with hand-typeset Fraunces text.
- §3 Narrative arc: name the avatar transformation, NOT the
  step-by-step. Coach reels live or die on "did the viewer recognise
  themselves in the avatar in the first 3 seconds".
- §4 Visual style: name the surface (bookshelf, whiteboard, workshop
  room, walking shot, motion-graphic-only), the lighting, and the
  camera energy. If motion-graphic, name the typography (font family
  feel, weight, scale).
- §5 Audio role: coach reels split into two camps. Camp A: voice
  carries, no music, direct-to-camera. Camp B: minimal lofi at 10 to
  15% under VO. Name which.
- §6 Payoff: coach reels pay off on "the viewer feels they now know
  the shortcut" (saves), NOT on a punchline. The save-bait is usually
  a single screenshot-able line.
- §8 Why it went viral: coach reels almost always trigger
  identity-confirmation (viewer sees themselves in the avatar) or
  save-bait (one screenshot-able framework line). Name which.

For Greg Isenberg style references specifically:
- Cross-reference a proven short-form hook formula (your own swipe file or a creator framework you trust)
  for the 7-beat skeleton
- Identify which of Greg's 6 hook archetypes applies (or note "new variant")
- Tag the motion-graphic primitives from ~/.claude/skills/motion-graphic-reels/references/motion-vocabulary.md
  (MascotStar, FilePill, DocCard, BranchTree, PromptBar, etc.)

Write the output to deconstruction.md. Voice-grade through content-engine
and humanizer.
```

---

## Prompt 2: Rebuild for the brand (Path A Step 4, Skeleton 4)

```
You are running Step 4 of higgsfield-viral-replicator Path A. Rebuild
the deconstructed reel for {{BRAND_NAME}}, an online coach / course
brand.

Brand context: paste the "Brand context block" from brief.md.

Use templates/rebuild-prompt-skeleton.md (Skeleton 4) as the canonical
structure. Produce three deliverables:

1. Shot-by-shot rebuild table in rebuild.md
   - Beat number, duration (sec), shot description, on-screen text,
     audio, "what mechanic we are keeping from the original"
   - 5 to 7 beats total for a 30 to 45 second reel (coach reels are
     typically longer than DTC because the framework needs more time)

2. Paste-ready Higgsfield prompt for the DOMINANT shot in higgsfield.md
   - Use Skeleton 4 format
   - Coach-specific fills:
     - DURATION: 5 to 8 seconds, 9:16 vertical
     - SUBJECT + ACTION: ONE action only. "Coach walks into workshop
       room and sets notebook on table" not "walks in AND opens
       notebook AND turns to camera"
     - SETTING: workshop room with bare walls, home office with
       bookshelf, walking shot in laneway. Pick one. NEVER a hotel
       lobby flex, NEVER a luxury-car backdrop.
     - LIGHTING: "soft late-afternoon window light from screen-left"
       or "calm overhead daylight, no key light"
     - CAMERA: "slow handheld push-in covering 6 inches over the
       duration" OR "static lock-off mid-shot" (same pattern as the
       original)
     - COLOR PALETTE: 3 anchors max from brand block. Selr AI default:
       cream walls, dark wood table, single purple notebook accent
     - AUDIO INTENT: "ambient room tone and coach voice direct
       unhurried no music" (Selr AI default)
     - BRAND VISIBILITY: "notebook stays in frame from 0:02, brand
       cover readable in final 1.5 seconds"
     - EXCLUDE: universal anti-slop block PLUS
       "rented luxury cars, hotel-lobby backdrops, Wolf-of-Wall-Street
       energy, gradient overlays, drop shadows, on-the-nose flexing,
       income-promise overlays"

3. Caption draft in rebuild.md
   - ≤200 chars before the cutoff, then 1 to 2 sentence expansion
   - Coach voice from brand block, not generic guru voice
   - Soft CTA only. Use "the free resource at [URL]" or "the workshop
     dates if you want the install" or "the playbook if you want the
     framework". NEVER "DM me 'INFO'", NEVER "limited spots" without
     a real date.

Rebuild rules:
- KEEP from original: hook archetype, beat cadence, payoff shape,
  save-bait line structure
- CHANGE from original: subject, exact words, music, on-screen text,
  signature framework name
- One mechanic per rebuild. If the original stacked authority +
  receipt + contrarian, pick the one that maps cleanest to
  {{BRAND_NAME}}'s real evidence (do we have a Stripe receipt? a real
  client outcome? a real install count?)
- Resist on-the-nose. If the original was Greg breaking down a
  community-business framework, don't rebuild as "the founder breaks down a
  community-business framework". Translate the mechanic to Selr AI's
  real domain (workshop installs, AI-ops, GHL setups).

Voice-grade every text output through content-engine + humanizer
before saving.
```

---

## Prompt 3: Handoff dispatcher (Path A Step 6)

```
You are running Step 6 of higgsfield-viral-replicator Path A. Decide
which downstream reel skill assembles the full reel and write the
handoff note.

Coach reel handoff selection rule:

| Rebuild visual style | Hand off to |
|---|---|
| Greg-style motion-graphic typography (Fraunces text, named primitives, no face) | motion-graphic-reels |
| Direct-to-camera coach, AI face (rebuilt for a brand that isn't filming themselves) | cinematic-ai-reels |
| Direct-to-camera coach, real face (brand is filming themselves, e.g. a founder filming for their own brand) | frontcam-reels |
| Mixed (face plus motion-graphic overlays) | cinematic-ai-reels + motion-graphic-reels overlay pass (or frontcam-reels + motion-graphic-reels for Selr AI) |

Fallback rule: if cinematic-ai-reels is not installed, route to
frontcam-reels and document the deviation in handoff.md.

Selr AI override: the founder films themselves, so for any Selr AI rebuild
default to frontcam-reels (real face) with a motion-graphic-reels
overlay pass for any on-screen text or branded primitives.

Write handoff.md with:
- Which reel skill to load next
- Path to deconstruction.md
- Path to rebuild.md
- Path to higgsfield.md
- The 7-beat script skeleton tagged onto the rebuild table (if Greg-style)
- Any coach-specific deviations (e.g. "this rebuild needs a real
  client receipt screenshot inserted at beat 4, source TBD")
- One-line summary suitable for ~/board/_log.md

Do NOT auto-invoke the downstream skill.
```
