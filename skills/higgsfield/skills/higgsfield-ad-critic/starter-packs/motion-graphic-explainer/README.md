# Starter pack, motion-graphic explainer (SaaS / indie hacker)

## What this is

A worked example of a motion-graphic explainer critique loop for a micro-SaaS or indie-hacker launch video. Use it to see how `higgsfield-ad-critic` catches the failure mode that wrecks 90% of SaaS launch videos: aha-moment lands too late and the CTA does not name the URL.

## How to use in 60 seconds

1. **Render the example.** Open `example-ad-source.md`, copy the Higgsfield rebuild prompt, paste into Higgsfield Vibe Motion, render at 9:16, 20 seconds. Save the MP4 anywhere.
2. **Hand the MP4 to the skill.** In Claude Code, run the `higgsfield-ad-critic` skill and pass the file path along with the intent brief (which notes this is a Vibe Motion render so Section 3 is skipped). The skill writes a critique markdown to `~/board/_active/ad-critic-YYYY-MM-DD/`.
3. **Compare to the sample.** Read `critique.md` in this folder. The skill's output on your render will look very similar (same slow-pacing finding, same late-aha warning, same "link in bio" CTA flag).
4. **Apply the revision.** Use `revision-prompt.md` to re-render. Total time: 2-5 minutes per loop.

## Cost

- Higgsfield (native virality_predictor path): 0-20 credits. Free on Ultra plan. Note: virality_predictor works on Vibe Motion exports the same way it does on Seedance exports.
- Gemini fallback path (if Higgsfield MCP is not connected): a few cents per critique on the Gemini Files API free tier.
- A 20-second 720p render uses 1 upload request + 1 generate request.

## Pattern D applies

This is a Vibe Motion render (code-based graphics). Per the parent skill, **Section 3 (visual artifacts) is skipped** because Vibe Motion does not produce pixel-prediction artifacts like head morphs or hand glitches. The remaining four sections (hook, pacing, voice, CTA) all apply.

## What this pack proves

- The critic catches the "aha lands too late" failure mode. Most SaaS founders look at their video and feel the story is right without realising the retention window has already closed by the time the aha lands.
- The critic flags "link in bio" as the wrong CTA for cross-platform launch videos and forces the URL to be named.
- The critic compresses 20-second cuts to 15-second cuts when the story can carry it. Cuts that hit retention windows ship; cuts that overrun lose distribution.

## Files in this pack

- `example-ad-source.md`, the source prompt (Vibe Motion format) and what the rendered ad represents.
- `critique.md`, the sample critique (Pattern D applied, Section 3 skipped).
- `revision-prompt.md`, the rewritten Vibe Motion prompt compressed from 20s to 15s.
- `sample/`, populated in Phase 4 with the actual rendered MP4.
- `README.md`, this file.

## When to reach for this pack

When the user is building any of these:

- Micro-SaaS launch video ($9-49/mo)
- B2B SaaS explainer ($99-499/mo per seat)
- Indie Hackers Product Hunt launch video
- AppSumo or lifetime-deal launch spot
- Vertical SaaS demo or before-after workflow comparison
- Any explainer where the founder face is NOT on screen and the product UI is the hero

If the user is building a UGC product ad or a founder-to-camera talking head, route to one of the other two starter packs in this folder instead.
