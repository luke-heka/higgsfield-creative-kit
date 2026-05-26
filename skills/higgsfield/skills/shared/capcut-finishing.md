# CapCut Finishing Recipe (Higgsfield → Final Cut)

Universal post-production fixes applied AFTER Higgsfield renders any
multi-chunk video. Extracted from real workflows (Alex Robinson UGC,
THE ECOM KING Marketing Studio).

Loaded by `higgsfield-ugc-ads`, `higgsfield-marketing-studio`,
`higgsfield-content-factory` (when assembling a video carousel cover).

---

## When To Use This

You have rendered multiple Higgsfield clips (3-6 chunks of UGC, multi-format
ad components, etc.) and need to assemble + polish them into a single
posted video.

If you're working with a single 5-8s clip, skip CapCut and post direct.

---

## Universal Pipeline

```
Higgsfield chunks (downloaded as MP4)
  ↓
CapCut: import all clips to timeline in order
  ↓
Speed adjust per clip (80-90% if AI rushed delivery)
  ↓
B-roll overlay for hallucination repair (cover bad frames)
  ↓
Audio sync + mute hallucinated audio sections
  ↓
Auto-captions (Classic preset, branded color, raised position)
  ↓
Export 1080p H.264 9:16 (or 1:1 for square)
```

---

## Fix 1 — Rushed Delivery (most common)

**Symptom:** AI voiceover speaks too fast, words run together, energy reads
unnatural.

**Fix:**
1. Select the clip on the timeline.
2. Right-click → Speed → Normal.
3. Set speed to **80-90%** (not lower — voice pitch drops noticeably below
   80%).
4. Audio pitch is preserved automatically in modern CapCut.

**When to regenerate instead:** if the chunk runtime is already longer than
the script needs, regenerate with a shorter runtime parameter rather than
slowing in post.

---

## Fix 2 — Hallucinated Frames (head suddenly enlarges, hand bends wrong)

**Symptom:** 1-3 second window where the AI generation visibly breaks
character / anatomy / physics. Common at clip transitions.

**Fix:**
1. Identify the bad seconds (scrub frame-by-frame).
2. Find a clean 1-3 second slice from another chunk (unboxing B-roll,
   product close-up, brand metric animation).
3. Drag that slice onto the timeline ABOVE the broken section as a
   picture-in-picture / overlay layer.
4. Trim the overlay to exactly cover the broken seconds.
5. **Mute the overlay's audio track** (so the voiceover from the main
   chunk continues uninterrupted).

This is faster than regenerating an entire chunk and reads naturally as
intentional editing.

---

## Fix 3 — Voice Inconsistency Across Chunks

**Symptom:** Chunk 2's voice has different timbre/accent than Chunk 1's
voice. AI didn't lock voice across generations.

**Fix path A (Higgsfield-side, before CapCut):**
1. In Higgsfield, open the offending clip.
2. Click **Change Voice**.
3. Pick the voice that matches the rest of your chunks.
4. Apply, re-download.

**Fix path B (CapCut-side, when path A fails):**
1. Strip the audio from the bad chunk entirely.
2. Re-record voiceover in one take covering all the bad sections.
3. Sync to the visual timeline.

Path A is faster and cheaper (no new credits).

---

## Fix 4 — Captions That Look Generic

**Symptom:** Default CapCut captions look like every other AI ad.

**Fix:**
1. Auto-captions → Generate.
2. Style → **Classic preset** (not "Cinematic", not "Tiktok").
3. Enable **black outline** (1-2px) — survives any background.
4. Set position to **raised** (~25-30% from bottom, not at the very edge
   where the IG/TikTok UI overlaps).
5. Pick ONE brand-aligned color and stick with it:
   - White + black outline (universal, safest)
   - Yellow + black outline (high-energy ads)
   - Purple + white outline (Selr AI brand)
6. Font: stick with default sans-serif. Stylised fonts at scale = AI tell.

---

## Fix 5 — Pacing Too Slow

**Symptom:** Final video drags, watch-time data suggests viewers drop at
mid-clip.

**Fix:**
1. **Cut the first 1-2 seconds** of each chunk if the AI did a slow
   "set-up" beat. Higgsfield often warms up before the action.
2. **Cross-dissolve transitions** between chunks (0.3s max) so cuts feel
   intentional, not abrupt.
3. **Speed up B-roll chunks** to 110-120% — viewers know B-roll is filler,
   tolerate faster pace.
4. Keep the talking-head/UGC chunks at 80-100% — these carry the message.

---

## Brand Caption Color Picker (Selr AI defaults)

| Use case | Primary color | Outline |
|---|---|---|
| Selr AI carousel reel covers | Purple #7B61FF | White |
| Workshop ad UGC | Yellow #FFD400 | Black |
| Skool community drops | Black | White (if dark BG) / no outline (if light) |
| Generic / client work | White | Black 2px |

---

## Export Settings

| Platform | Resolution | Aspect | Framerate | Bitrate | Codec |
|---|---|---|---|---|---|
| Instagram Reels | 1080×1920 | 9:16 | 30fps | 8 Mbps | H.264 |
| Instagram Feed | 1080×1080 | 1:1 | 30fps | 8 Mbps | H.264 |
| TikTok | 1080×1920 | 9:16 | 30fps | 10 Mbps | H.264 |
| YouTube Short | 1080×1920 | 9:16 | 30fps | 12 Mbps | H.264 |
| LinkedIn | 1080×1080 | 1:1 | 30fps | 8 Mbps | H.264 |

Never export at 4K for Higgsfield-sourced content — it amplifies AI
artifacts. 1080p is the sweet spot.

---

## QuickTime Compatibility Check

Before posting to Mac-edited workflows or showing in QuickTime:

1. Export with **H.264 codec** (not H.265/HEVC — Higgsfield's clips can
   ship with metadata QuickTime mishandles).
2. Open in QuickTime Player. Scrub the timeline. If it stutters or refuses
   to play, re-export from CapCut with **Faststart MOOV atom** enabled.

This is the same fix the `frontcam-reels` skill applies for talking-head
exports.
