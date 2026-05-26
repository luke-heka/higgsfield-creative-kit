# Chunk Prompt Template

**Purpose:** Field-by-field skeleton for a single chunk's Seedance 2.0 render
prompt. Combines the universal direction block (from
`templates/universal-direction-block.md`) with the chunk-specific fields from
`templates/multi-chunk-script.yaml`.

**Use:** Filled in once per chunk by Chat 2. Saved as
`chunks/chunk-{N}-prompt.md`. Pasted verbatim into Higgsfield Seedance 2.0
prompt input during Phase 5.

---

## Template (verbatim, fill the [bracketed] fields)

```
=== UNIVERSAL DIRECTION ===

[Paste the entire universal direction block from
templates/universal-direction-block.md, with all fields filled from the YAML.]

=== CHUNK {N}, {ROLE} ===

VOICEOVER (read by [character_lock.voice], apply via Change Voice button)
"[chunks[N].voiceover]"

RUNTIME
{chunks[N].runtime}s
Note: Do NOT let Seedance speed up delivery to fit. If the voiceover doesn't
fit naturally in this runtime, return to Chat 2 and shorten the voiceover.
A rushed delivery is the #2 AI-look tell after character drift.

PRODUCT VISIBILITY
{Yes / No}
{If Yes:} Product Element tag: [chunks[N].product_tag], confirm @product is
loaded in Higgsfield Elements panel before generating.
{If No:} Product Element tag: NONE, REMOVE @product from the Elements panel
BEFORE generating this chunk. Otherwise the model hallucinates the product
into the shot.

FRAMING
[chunks[N].framing]
(Specific body part the camera focuses on, specific angle, specific distance.
Avoid "medium shot" alone, name what's in frame and what's out.)

CAMERA MOVEMENT
[Pick ONE from this list that fits the role:]
- handheld follow (subject moves, camera follows in selfie style)
- slow push-in (camera slowly moves toward subject's face, use sparingly,
  for proof or CTA chunks)
- static handheld (no movement, but wobble, default for most chunks)
- slight pan (camera pans 5–10 degrees, for solution reveal chunks)
- whip pan in (rapid 30-degree pan that lands on subject, for hook only,
  use sparingly)

LIGHTING
[Inherit from universal_directions.b_roll. Mention the specific direction
of the light source, e.g. "soft natural light through a window at
camera-right, no fill, no key, no rim".]

MOOD
[Match the role:]
- hook: intrigue, slight smile, eyes wide enough to read as engaged
- problem: subtle frustration, brows lightly furrowed, looking off-camera
- agitation: visible concern, no smile, more downward gaze
- solution: relief, slight upward gaze, small smile starting
- mechanism: focused, holding product at angle to show spec/label
- proof: confident, direct eye contact, micro-smile
- demo: focused on the demonstration, not the camera
- cta: direct eye contact with lens, clear, no hard sell vibe

CHUNK-SPECIFIC EXCLUDE (additional to universal exclude list)
{Pick the ones that apply to this chunk:}
- "perfect spokesperson delivery", for any chunk
- "infomercial energy", especially for CTA
- "fake enthusiasm", for solution/proof chunks
- "product hero shot with rim light", when include_product is true (we
  want UGC handheld, not e-commerce)
- "before-after split screen", unless explicitly demoed in this chunk
- "text overlays", captions added later in CapCut
```

---

## Per-role specifics

Each role has slightly different prompt nudges. Apply on top of the template.

### Role: hook (Chunk 1)

- Voiceover MUST stand alone, no setup, no "so anyway", no "the other day".
- Framing: tighter than other chunks (shoulders + face fills frame). Pulls
  the viewer in.
- Mood: intrigue. NOT a smile, a smile reads as influencer-sponsored.
- Camera: static handheld or whip pan in. NOT slow push-in.
- Background: minimal, don't compete with the hook.
- Product: NEVER visible. Holding back creates curiosity.

### Role: problem (Chunk 2)

- Voiceover: ONE specific painful moment, present tense, first person.
- Framing: slightly lower angle, less direct eye contact.
- Mood: subtle frustration. Not theatrical, UGC realism.
- Camera: static handheld.
- Background: same as universal, may have a "frustration prop" in frame
  (cluttered desk, full inbox screen, broken thing).
- Product: NEVER visible.

### Role: agitation (Chunk 3, full-stack only)

- Voiceover: what happens if the problem stays unsolved. Concrete cost,
  time, or risk.
- Framing: medium shot, character looks away thoughtfully.
- Mood: visible concern. Still subtle, still UGC.
- Camera: static handheld with slight reframe.
- Product: NEVER visible.

### Role: solution (Chunk 3 mid-funnel / Chunk 4 full-stack)

- Voiceover: "Then I tried [product name]..." or similar. NAMES the product.
- Framing: character reaches off-screen and brings product into frame.
- Mood: shift to relief. Small smile starting.
- Camera: slight pan as product enters frame.
- Background: same as universal.
- Product: VISIBLE. `@product` tag MUST be loaded.

### Role: mechanism (Chunk 5, full-stack only)

- Voiceover: WHY it works. Names specific ingredient / feature / spec.
- Framing: medium close-up. Product held at angle so label/spec is readable.
- Mood: focused, slightly more serious than solution chunk.
- Camera: static handheld or very slow push-in (10% zoom over 10s).
- Background: same.
- Product: VISIBLE + angled so spec face is readable.

### Role: proof (Chunk 4 mid-funnel / Chunk 6 full-stack)

- Voiceover: specific named result. No hype. Past tense if a result, present
  if a habit.
- Framing: subject demonstrates product use (uncapping, applying, opening).
- Mood: confident, direct eye contact.
- Camera: static handheld with one reframe to show the demonstration.
- Background: same.
- Product: VISIBLE, in active use.

### Role: demo (alternative to proof)

- Same as proof but visual demonstration is the focus, not voiceover.
- Voiceover may be shorter (≤15 words) and let the action speak.

### Role: cta (last chunk)

- Voiceover: clear single action + URL or offer.
- Framing: selfie handheld, product held up to camera at chest height,
  direct eye contact with lens.
- Mood: direct, friendly, not infomercial.
- Camera: static handheld.
- Background: same.
- Product: VISIBLE, held up.

---

## Camera movement library (pick one per chunk)

| Movement | When | Avoid |
|----------|------|-------|
| Static handheld | Most chunks, default | When you need motion to add energy |
| Handheld follow | Subject moves through space | When subject is stationary |
| Slow push-in | Proof chunk, CTA chunk | Hook chunk (feels staged) |
| Slight pan | Solution chunk product reveal | Hook chunk |
| Whip pan in | Hook chunk only (rare) | Any other chunk |
| Slow pull-back | Almost never | All chunks (loses intimacy) |
| Dolly orbit | Never in UGC | Always (feels cinematic, not UGC) |

For the full camera-movement vocabulary, see `higgsfield-camera` (sibling
skill).

---

## Mood-vocabulary translation

When the YAML role says one thing but the model interprets it as something
else, use these explicit translations in the chunk prompt:

| Role | Don't say | Do say |
|------|-----------|--------|
| hook | "engaging" | "wide-eyed, slight smile, eyes scan back to lens" |
| problem | "frustrated" | "brows lightly furrowed, mouth tight, looking off-camera at the source of frustration" |
| solution | "happy" | "relief lifting the shoulders, small smile starting at the corners of the mouth" |
| proof | "confident" | "direct eye contact, micro-smile, slight nod" |
| cta | "compelling" | "direct lens eye contact, soft smile, clear consonants in delivery" |

Generic mood words ("happy", "confident") get interpreted differently each
render. Specific physical descriptions render consistently.

---

## Pre-render check (run before pasting into Higgsfield)

- [ ] Universal direction block is at the top
- [ ] CHUNK header has the right N and role
- [ ] Voiceover word count matches the role cap
- [ ] Runtime matches the YAML
- [ ] Product visibility matches `include_product` in YAML
- [ ] Elements panel has `@product` loaded (or removed) per visibility
- [ ] Framing names a specific body part and angle, not just "medium shot"
- [ ] Camera movement is named from the library above
- [ ] Mood is described physically, not abstractly
- [ ] Exclude list includes the universal exclude PLUS chunk-specific items
- [ ] No em dashes anywhere in the prompt
- [ ] No banned vocab anywhere in the prompt
- [ ] Aspect 9:16, resolution 720p

If any box is unchecked, fix before generating. Each Higgsfield render at
720p costs ~3-5 credits, pre-flight is free.
