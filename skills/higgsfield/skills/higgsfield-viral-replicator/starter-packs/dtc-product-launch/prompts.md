# DTC Product Launch: Ready-to-Use Prompts

> Three prompts. Run them in order. Each one assumes the variables from
> `brief.md` are filled.

---

## Prompt 1: Deconstruct the viral reference (Path A Step 2)

Paste this into Claude after you have scraped the viral post and have
`raw-post.json` written to the output folder.

```
You are running Step 2 of higgsfield-viral-replicator Path A for a DTC
ecommerce brand.

Read raw-post.json in the current output folder. Produce a 9-section
deconstruction using the exact schema in
~/.claude/skills/higgsfield/skills/higgsfield-viral-replicator/templates/deconstruction.md.

Fill EVERY field. Special attention for DTC:
- §1 Hook archetype: pick from problem-aware, contrarian, curiosity-gap,
  story-in-1-sentence, claim-then-prove, visual-mismatch, specific-number.
  DTC almost always lands on claim-then-prove or problem-aware. If you
  pick something else, explain why in one sentence.
- §2 Pattern interrupts: DTC winners use 1 to 3 cuts MAX in the first
  6 seconds. If the reference has more, flag it as "high-cut style,
  may need to thin out for the rebuild".
- §4 Visual style: name the surface (bathroom, kitchen, vanity, bedside),
  the lighting (soft window, ring light, natural daylight), and the
  camera energy (phone-prop static, handheld selfie, over-shoulder).
- §5 Audio role: DTC winners either use ASMR product sound (no music)
  OR a trending TikTok audio at 30 to 40% volume under a VO. Name which.
- §6 Payoff: for DTC the payoff is almost always (a) product label
  readable, (b) before-vs-after visible, or (c) founder face plus
  product in same frame. Name which.
- §8 Why it went viral: DTC winners almost always trigger save-bait
  (a screenshot-able single line) or curiosity-gap-resolution (the
  ingredients reveal). Name the mechanic specifically.

Write the output to deconstruction.md in the current folder. Voice-grade
through content-engine and humanizer before saving.
```

---

## Prompt 2: Rebuild for the brand (Path A Step 4, Skeleton 4)

Paste this after the deconstruction is locked.

```
You are running Step 4 of higgsfield-viral-replicator Path A. Rebuild
the deconstructed video for {{BRAND_NAME}}, a DTC ecommerce brand.

Brand context: paste the "Brand context block" from brief.md.

Use templates/rebuild-prompt-skeleton.md (Skeleton 4) as the canonical
structure. Produce three deliverables in this order:

1. Shot-by-shot rebuild table in rebuild.md
   - Beat number, duration (sec), shot description, on-screen text,
     audio, and "what mechanic we are keeping from the original" column
   - 3 to 5 beats total, mapped to the original's narrative arc

2. Paste-ready Higgsfield prompt for the DOMINANT shot only in higgsfield.md
   - Use Skeleton 4 format
   - DTC-specific fills:
     - DURATION: 5 to 8 seconds, 9:16 vertical
     - SETTING: bathroom counter, kitchen counter, or bedside (per brand block)
     - LIGHTING: "soft natural window light from screen-left at golden hour"
       (DTC winners never use ring lights or studio key)
     - CAMERA: "phone propped on stand, locked-off, no movement"
       OR "handheld selfie with slight natural wobble" (pick one,
       same pattern as the original)
     - COLOR PALETTE: 3 anchors max, pulled from the brand block
     - BRAND VISIBILITY: "product enters frame at 0:02, label readable
       by final 1.5 seconds"
     - EXCLUDE: append the universal anti-slop block PLUS
       "studio lighting, ring-light reflection in eyes, 4K cinema look,
       stock-photography poses, shop-now overlay card, brand logo bug"

3. Caption draft in rebuild.md
   - ≤200 chars before the cutoff, then 1 to 2 sentence expansion
   - Customer voice not brand voice. Lowercase opener allowed.
   - Soft CTA only. NEVER "shop now", NEVER "DM me", NEVER "link in bio"
     as the primary CTA. Instead: "the [PRICE] bundle if you want the
     full set" or "back in stock if you missed it last time".

Rebuild rules:
- KEEP from original: hook archetype, cut cadence, payoff shape,
  product-visibility timing
- CHANGE from original: subject, exact words, music, on-screen text,
  product
- One mechanic per rebuild. If the reference stacked 3 mechanics
  (e.g. claim-then-prove + ASMR + founder-face), pick the one that
  maps cleanest to {{BRAND_NAME}}'s current asset library
- Resist on-the-nose. Don't rebuild "skincare cream on hand" as
  "supplement powder on hand". Translate the mechanic, not the surface.

Voice-grade every text output through content-engine + humanizer before
saving. If either gate fails, rewrite the failing lines.
```

---

## Prompt 3: Handoff dispatcher (Path A Step 6)

Paste this last.

```
You are running Step 6 of higgsfield-viral-replicator Path A. Decide
which downstream reel skill assembles the full ad and write the handoff
note.

DTC handoff selection rule:

| Rebuild visual style | Hand off to |
|---|---|
| Real-person face + real product B-roll (default DTC) | cinematic-ai-reels |
| 100% text-on-screen "before vs after" or "ingredients breakdown" | motion-graphic-reels |
| AI-narration voice-over with no on-screen face | notebook-reels |
| Real founder face only, no AI rendering needed | frontcam-reels |

Fallback rule: if cinematic-ai-reels is not installed (check
`ls ~/.claude/skills/cinematic-ai-reels`), route to frontcam-reels and
document the deviation in handoff.md.

Write handoff.md with:
- Which reel skill to load next
- Path to deconstruction.md
- Path to rebuild.md
- Path to higgsfield.md
- Any DTC-specific deviations (e.g. "this rebuild needs a separate
  product-on-white close-up rendered through nano-banana before the
  cinematic-ai-reels assembly")
- One-line summary suitable for ~/board/_log.md

Do NOT auto-invoke the downstream skill. The user explicitly runs it
next.
```
