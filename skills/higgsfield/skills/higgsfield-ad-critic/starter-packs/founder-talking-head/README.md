# Starter pack, founder talking head (coach / consultant)

## What this is

A worked example of a founder-to-camera ad critique loop for a coach, course creator, or consultant. Use it to see how `higgsfield-ad-critic` catches the failure mode that wrecks 80% of AI-rendered talking-head ads: technically correct delivery that reads as scripted, not spoken.

## How to use in 60 seconds

1. **Render the example.** Open `example-ad-source.md`, copy the Higgsfield rebuild prompt, paste into Higgsfield Seedance 2.0 or Cinema Studio, render at 9:16, 15 seconds. Save the MP4 anywhere.
2. **Hand the MP4 to the skill.** In Claude Code, run the `higgsfield-ad-critic` skill and pass the file path. The skill writes a critique markdown to `~/board/_active/ad-critic-YYYY-MM-DD/`.
3. **Compare to the sample.** Read `critique.md` in this folder. The skill's output on your render will look very similar (same flat-delivery finding, same robotic-blink artifact, same DM-bait CTA warning).
4. **Apply the revision.** Use `revision-prompt.md` to re-render. Total time: 2-5 minutes per loop.

## Cost

- Higgsfield (native virality_predictor path): 0-20 credits. Free on Ultra plan.
- Gemini fallback path (if Higgsfield MCP is not connected): a few cents per critique on the Gemini Files API free tier.
- A 15-second 720p render uses 1 upload request + 1 generate request.

## What this pack proves

- The critic catches the delivery-not-script failure mode. Most coaches re-write the script when the real problem is the performance.
- The critic flags DM-bait CTAs (a 2026 TikTok/Reels demotion trigger) that most coaches do not know to look for.
- The critic identifies the bookshelf-behind-coach background as an AI pattern-match and routes the user to a less-copied frame.

## Files in this pack

- `example-ad-source.md`, the source prompt (Skeleton 2 format) and what the rendered ad represents.
- `critique.md`, the sample critique structured exactly like the skill's live output.
- `revision-prompt.md`, the rewritten Higgsfield prompt with explicit delivery direction.
- `sample/`, populated in Phase 4 with the actual rendered MP4.
- `README.md`, this file.

## When to reach for this pack

When the user is building any of these:

- Online coach Reels or TikTok ad ($97-$5K offers)
- Course creator launch video
- Consultant or service-business founder-to-camera spot
- Cohort, mastermind, or workshop promo
- Any face-on-camera ad where the founder is the only on-screen subject

If the user is building a UGC product ad or a motion-graphic SaaS explainer, route to one of the other two starter packs in this folder instead.
