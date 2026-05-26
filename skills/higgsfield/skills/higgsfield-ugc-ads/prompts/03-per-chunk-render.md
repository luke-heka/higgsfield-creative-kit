# Prompt 03: Per-chunk render ritual

**Purpose:** The operational ritual for rendering each chunk in Higgsfield
Seedance 2.0. Read this before generating Chunk 1. Re-read between every
chunk if you've been away from the tool for >10 minutes.

**Use in:** Phase 5 of the workflow (after Chat 2 emits the YAML + per-chunk
render blocks). Repeats N times, once per chunk.

---

## Pre-flight check (before opening Higgsfield)

Confirm these exist on disk:

- [ ] `~/board/_active/ugc-ads-<date>/00-product-still.png` (clean product render)
- [ ] `~/board/_active/ugc-ads-<date>/01-character-ref.png` (character reference)
- [ ] `~/board/_active/ugc-ads-<date>/02-script.yaml` (canonical script)
- [ ] `~/board/_active/ugc-ads-<date>/chunks/chunk-{N}-prompt.md` for every N

If any are missing, do NOT generate. Return to the relevant phase first.

---

## Element tag setup (one-time, before Chunk 1)

In Higgsfield:

1. Open Seedance 2.0 (higgsfield.ai → Seedance 2.0 tab).
2. Open the **Elements** panel.
3. Upload `00-product-still.png`.
4. Tag the upload as `@product` (or whatever tag your `02-script.yaml`
   uses, `@bottle`, `@app`, `@device` etc).
5. Confirm the tag appears in the autocomplete when you type `@` in a
   prompt box.

This is the multi-chunk consistency lever. Skipping it = the product
hallucinates a different shape per chunk.

For canonical Element tagging mechanics, see
`../shared/element-tagging.md`.

---

## Character setup (one-time, before Chunk 1)

Three paths, matching `character_lock` in the YAML:

**Path A, Higgsfield avatar by name:**
- In the chunk prompt, reference the avatar by name (e.g. "Megan, [appearance
  description from YAML]").
- No upload needed.

**Path B, Soul ID:**
- Confirm the Soul ID is loaded in the workspace.
- See `higgsfield-soul` for Soul ID load mechanics.
- Reference the Soul ID in every chunk prompt.

**Path C, Uploaded reference:**
- In the chunk prompt input, upload `01-character-ref.png` as a reference.
- Higgsfield's reference-image input slot accepts one image per generation.
- The reference image needs to be re-attached PER CHUNK because Seedance
  doesn't persist references across chats in the standard UI.

Document which path was used in `06-brief.md` so future-you can audit.

---

## Per-chunk render loop (REPEAT N TIMES)

For each chunk in order (1, 2, 3...):

### Step 1: Open the chunk prompt file

```
cat ~/board/_active/ugc-ads-<date>/chunks/chunk-{N}-prompt.md
```

### Step 2: Check `include_product` and adjust the Elements panel

- If `include_product: true` → confirm `@product` is in the Elements panel.
- If `include_product: false` → REMOVE `@product` from the Elements panel
  BEFORE generating. Otherwise Seedance hallucinates the product into the
  shot.

This is the single most-skipped step. Costs ~3 credits per missed removal.

### Step 3: Paste the full prompt block

Copy the entire chunk-{N}-prompt.md content (universal direction + chunk
block + EXCLUDE list) into the Seedance prompt input.

### Step 4: Set generation parameters

| Setting | Value |
|---------|-------|
| Aspect | **9:16** |
| Resolution | **720p** (iteration), set 1080p ONLY for the final master pass |
| Duration | Match `chunks[N].runtime` exactly (4s, 6s, 8s, 10s) |
| Mode | **Image-to-video** if you have a reference image attached, else **Text-to-video** |
| Voice | Will be applied via Change Voice button after first render |

### Step 5: Generate

Plus plan ($49/mo) allows 4 chunks in parallel. You can start Chunks 1–4
simultaneously if you have all 4 prompt files ready.

### Step 6: Wait + diagnose

| Render time | Diagnosis | Action |
|-------------|-----------|--------|
| <10s, returns "flagged" | Content filter rejection | DO NOT regenerate. Apply `higgsfield-seedance` 6-slot formula rewrite. Re-paste. |
| >30s, returns "failed" | Render infrastructure | Cut action density. Shorten runtime by 2s. Retry. |
| Completes, looks wrong | Render succeeded, output is off | See diagnostic table below. |
| Completes, looks right | Ship it | Continue. |

### Step 7: Voice pass (after first successful render of Chunk 1)

Once Chunk 1 lands with a voice you like, apply that same voice to every
subsequent chunk via the **Change Voice** button. Do NOT regenerate to fix
voice, Change Voice is one click and reuses the existing video.

### Step 8: Download

Save to `~/board/_active/ugc-ads-<date>/chunks/chunk-{N}.mp4`.

### Step 9: Move to next chunk

Repeat for chunk N+1.

---

## Diagnostic table, "render succeeded but looks wrong"

| Symptom | Cause | Fix |
|---------|-------|-----|
| Character looks like a different person | Reference not attached OR Soul ID not loaded | Re-attach reference / reload Soul ID. Regenerate. |
| Product looks like a different product | `@product` tag not loaded OR wrong tag in prompt | Re-confirm Elements panel. Regenerate. |
| Product appears in a no-product chunk | `@product` tag stayed in Elements | REMOVE the tag, regenerate. |
| Delivery rushed | Voiceover too long for runtime | Shorten the voiceover line in `02-script.yaml`, re-emit chunk prompt, regenerate. OR keep video and fix speed in CapCut to 80-90%. |
| Voice is different from other chunks | Auto-generated voice varies per render | Use Change Voice button, pick the voice from Chunk 1. |
| Looks too "AI" / too clean / no wobble | UGC realism notes missing or weak | Strengthen `universal_directions.ugc_realism_notes`, add "selfie handheld, slight wobble, imperfect framing, candid". Regenerate. |
| Background is wrong | `b_roll` instruction unclear | Make the b_roll instruction more concrete, name a specific room, light source, surface. Regenerate. |
| Head suddenly enlarges for 2s | Common Seedance artifact at >6s runtime | DO NOT regenerate. Fix in CapCut: overlay a B-roll snippet from another chunk + mute that section's audio. See `../shared/capcut-finishing.md`. |

---

## Cost-conscious render rules (the only rules that matter)

1. **720p always for iteration.** Only re-render at 1080p once the chunk is
   locked. Saves 50% per chunk.
2. **Don't regenerate for voice issues.** Use Change Voice. Costs 0 credits.
3. **Don't regenerate for short hallucinations.** Overlay in CapCut. Costs 0
   credits.
4. **Don't regenerate to upscale.** Re-render at the new resolution. Cleaner.
5. **Parallel up to 4 on Plus plan.** Don't wait for chunk N to finish
   before starting N+1 if you have all 4 prompts ready.
6. **Budget 1.5× planned credits.** ~30% of chunks need a regenerate.

---

## When to give up on a chunk and rewrite

If a chunk has been regenerated 3 times and still doesn't land, the prompt
is wrong, not the model. Go back to Chat 2 and rewrite the chunk's
voiceover + framing. Common rewrite patterns:

- Shorten the voiceover.
- Make the framing more specific (name the body part to focus on, not
  "medium shot").
- Move the product reveal earlier or later in the chunk.
- Swap the chunk's role (e.g. solution → proof) if the script structure
  is the actual issue.

Do not burn more than 3 retries on one chunk without going back to Chat 2.

---

## When all chunks are downloaded

- [ ] Confirm `chunks/chunk-1.mp4` through `chunks/chunk-N.mp4` all exist.
- [ ] Confirm each chunk's runtime matches the YAML.
- [ ] Confirm voice is consistent across all chunks (play 2s of each in
  order, if any sounds different, Change Voice that chunk).

Move to Phase 6, assembly per `../shared/capcut-finishing.md`.

---

## Optional, automate via seedance-pipeline

If `seedance-pipeline` is installed and Higgsfield MCP is connected via
`higgsfield-connector`, you can automate Phase 5:

```
For each chunk in 02-script.yaml:
  /skill seedance-pipeline
  Pass: chunk prompt + character reference + product Element tag + runtime
  Output: chunks/chunk-{N}.mp4
```

`seedance-pipeline` handles the Playwright / MCP dispatch + polling +
download. This skill emits the prompts; that skill renders them.

If MCP is not connected, fall back to the manual ritual above. The paste-ready
chunk prompts (Artefact 2 from Chat 2) work in either path.

---

## Hand off to Phase 6

Once all chunks are downloaded, move to CapCut assembly per
`../shared/capcut-finishing.md`. Do NOT skip the Phase 8 ship-gate
(`content-engine` + `humanizer`) on the final caption and on-screen text.
