# Starter pack, UGC product ad (DTC)

## What this is

A worked example of a UGC product ad critique loop for a DTC supplement, skincare, hair, or apparel brand. Use it to see how `higgsfield-ad-critic` turns a soft first-pass render into a SHIP-ready spot in one revision cycle.

## How to use in 60 seconds

1. **Render the example.** Open `example-ad-source.md`, copy the Higgsfield rebuild prompt, paste into Higgsfield Seedance 2.0, render at 9:16, 12 seconds. Save the MP4 anywhere.
2. **Hand the MP4 to the skill.** In Claude Code, run the `higgsfield-ad-critic` skill and pass the file path. The skill writes a critique markdown to `~/board/_active/ad-critic-YYYY-MM-DD/`.
3. **Compare to the sample.** Read `critique.md` in this folder. The skill's output on your render will look very similar (same failure modes, same directive verbs).
4. **Apply the revision.** Use `revision-prompt.md` to re-render. Total time: 2-5 minutes per loop.

## Cost

- Higgsfield (native virality_predictor path): 0-20 credits. Free on Ultra plan.
- Gemini fallback path (if Higgsfield MCP is not connected): a few cents per critique on the Gemini Files API free tier.
- A 60-second 720p render uses 1 upload request + 1 generate request. Comfortable for the daily-iteration use case.

## What this pack proves

- The critic catches the failure mode that wrecks most DTC UGC: soft hook + missing CTA + one show-stopping visual artifact in the first 5 seconds.
- The named directive system (STRENGTHEN_HOOK, RESHOOT_SHOT, RE_VOICE, TIGHTEN_CTA, ADD_BROLL, ADJUST_TIMING) maps every finding to a specific change in the next render.
- One re-render cycle is usually enough to take a v1 render from REVISE to SHIP.

## Files in this pack

- `example-ad-source.md`, the source prompt (Skeleton 2 format) and what the rendered ad represents.
- `critique.md`, the sample critique structured exactly like the skill's live output.
- `revision-prompt.md`, the rewritten Higgsfield prompt that addresses every directive.
- `sample/`, populated in Phase 4 with the actual rendered MP4.
- `README.md`, this file.

## When to reach for this pack

When the user is building any of these:

- DTC supplement, skincare, hair, or apparel UGC ad
- TikTok Shop ad
- Meta Advantage+ Shopping creative
- $25-120 AOV vertical with one creator and one product
- Anything that needs to look shot-on-phone, not shot-in-studio

If the user is building a founder-to-camera explainer or a motion-graphic spot, route to one of the other two starter packs in this folder instead.
