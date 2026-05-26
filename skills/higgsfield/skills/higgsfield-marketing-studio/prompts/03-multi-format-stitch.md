# Prompt 03. Multi-Format Stitch Render

Step 3 of the Marketing Studio orchestration. Goal: render the full
clip set with character + product consistency, one clip at a time, with
human gates between each clip so credits don't burn on a broken setup.

---

## Pre-flight gate

Before the first render:

- [ ] `00-brief.md` exists and confirmed.
- [ ] `01-format-list.md` exists with the final clip list.
- [ ] Avatar selected in Marketing Studio (the dropdown shows the chosen
      avatar name).
- [ ] Resolution slider set per tier: 720p for `cheap_test`, 1080p for
      `full_stitch`.
- [ ] Aspect ratio = 9:16 (vertical).
- [ ] Credit balance >= estimated credits in `01-format-list.md` + 30%
      overhead.
- [ ] Output folder exists.

If any gate fails, stop and fix. Do not start the loop with a broken
setup.

---

## The render loop

For each clip in `01-format-list.md` (CTA excluded, handled separately):

### Per-clip steps

1. **Open Marketing Studio.** Same product card loaded.
2. **Confirm avatar.** Same avatar selected. If you have to change the
   avatar between clips, stop, that's a setup error.
3. **Swap format dropdown** to the clip's format (UGC / Tutorial /
   Unboxing / Product Review / UGC Try-On Haul).
4. **Set duration** per the format list (15s default, 10s for Unboxing).
5. **Confirm resolution.** 720p for cheap_test, 1080p for full_stitch.
6. **Click Generate.** Wait 60-90 seconds. Render bar fills in real time.
7. **Watch the render.** Note any obvious hallucinations as they appear
   (face morph, hand glitch, product shape change).
8. **Download.** Save MP4 as `<output>/clip-<n>-<format>.mp4` (matches
   filename in format list).

### Per-clip human gate (MANDATORY)

After each clip downloads, before starting the next:

- [ ] Watch the clip end-to-end.
- [ ] Pass/fail against these checks:
  - Avatar face matches the previous clip
  - Product matches the product card image
  - Voiceover is coherent (not garbled)
  - No catastrophic hallucination (extra fingers, body warp, head
    morph mid-sentence) lasting more than 0.5s
  - Energy/tone matches the clip's role (UGC = casual; Tutorial =
    instructional; Review = considered)

**If pass:** proceed to next clip.

**If fail (minor):** note the issue in `<output>/cost-log.md`, plan to
cover with B-roll in CapCut (see `../../shared/capcut-finishing.md` Fix 2).
Proceed to next clip.

**If fail (catastrophic):** regenerate ONCE. If second render also fails:

- Format is wrong for this product (e.g. Unboxing for digital products
  that have no physical box). Drop the clip from the stitch.
- Avatar is wrong (e.g. female founder avatar for a male grooming
  product). Mint a new avatar via `prompts/04-avatar-strategy.md`,
  re-render from clip 1.
- Marketing Studio is having a bad day. Pause for 1 hour, retry.

Do not regen the same clip more than 2 times. Three regens = $0.30 lost
+ a broken stitch. Cut the clip or change the brief.

---

## The CTA clip (handled separately)

The CTA is NOT in Marketing Studio's format dropdown. Generate it via
direct Seedance using the template at `templates/cta-clip-prompt.md`.

1. Open the Seedance render panel (not Marketing Studio).
2. Same avatar selected from the avatar library (this is critical for
   face consistency with the stitched clips).
3. Paste the filled CTA prompt template.
4. Duration: 5s.
5. Resolution: matches the rest of the stitch.
6. Aspect: 9:16.
7. Generate, download as `<output>/clip-cta.mp4`.

The CTA copy itself ("Click the link below to shop now" or whatever the
campaign uses) must go through `content-engine` + `humanizer` BEFORE
becoming the prompt. Default Seedance CTAs sound generic.

---

## Cost log (write as you go)

Append to `<output>/cost-log.md` after each clip:

```markdown
| Clip | Format | Duration | Resolution | Credits | Regens | Notes |
|------|--------|----------|------------|---------|--------|-------|
| 1 | UGC | 15s | 1080p | 175 | 0 | First-pass pass |
| 2 | Tutorial | 15s | 1080p | 175 | 1 | First render had hand glitch, regen clean |
...
```

Final row should sum credits + regens. This is the spend receipt the
user can show their accountant / client / boss.

---

## Output

After the loop:

```
<output>/
├── clip-1-ugc.mp4
├── clip-2-tutorial.mp4
├── clip-3-unboxing.mp4
├── clip-4-review.mp4
├── clip-cta.mp4
└── cost-log.md (partial, assembly step appends final totals)
```

Proceed to `prompts/05-assemble-and-ship.md`.
