# Prompt 02. Format Selection

Step 2 of the Marketing Studio orchestration. Goal: pick the right
combination of clips for the campaign goal, in the right order, so the
final stitch actually converts.

---

## The five Marketing Studio formats

| Format | What it does | Best role in a stitch |
|--------|--------------|----------------------|
| **UGC** | Talking-head avatar holding the product, casual selfie style | Hook (clip 1) |
| **Tutorial** | Avatar demonstrating how to use the product | Demonstrate (clip 2) |
| **Unboxing** | Hands unboxing the product, no face | Proof (clip 3) |
| **Product Review** | Avatar speaking review-style about results | Social proof (clip 4) |
| **UGC Try-On Haul** | Avatar trying on fashion/wearables in series | Use for apparel |

The CTA clip is generated separately (5s, no Marketing Studio dropdown).
See `templates/cta-clip-prompt.md`.

---

## Goal-to-mix decision table

Read `00-brief.md` for the goal. Apply this table:

### Goal = `awareness`

Optimised for top-of-funnel: stop the scroll, plant the brand. Short
stitch (35s).

```
Clip 1, UGC (15s), hook
Clip 2, Tutorial (15s), demonstrate
Clip 3, CTA (5s), action
Total, 35s
```

### Goal = `conversion` (default)

The 4.6x ROAS recipe. Full 60s stitch. Compounds hook → demo → proof →
social-proof → action.

```
Clip 1, UGC (15s), hook
Clip 2, Tutorial (15s), demonstrate
Clip 3, Unboxing (10s), proof
Clip 4, Product Review (15s), social proof
Clip 5, CTA (5s), action
Total, 60s
```

### Goal = `retention`

For existing customers / re-engagement. Lead with proof + how-to. Drop
the hook UGC (they already know the brand).

```
Clip 1, Unboxing (10s), proof
Clip 2, Tutorial (15s), demonstrate
Clip 3, Product Review (15s), social proof
Clip 4, CTA (5s), action
Total, 45s
```

### Goal = fashion / apparel

Use Try-On Haul as the demonstration. Swap Tutorial for Try-On Haul.

```
Clip 1, UGC (15s), hook
Clip 2, UGC Try-On Haul (15s), demonstrate
Clip 3, Product Review (15s), social proof
Clip 4, CTA (5s), action
Total, 50s
```

---

## Cheap test override

If `iteration_tier = cheap_test`, ignore the full mix and render only
**2 clips**:

```
Clip 1, UGC (15s), hook
Clip 2, CTA (5s), action
Total, 20s
```

This is the throwaway hook-CTA combo. If THIS doesn't read as a usable
ad, the full stitch won't either. Kill and reshape the brief.

Cost: ~200 credits ≈ $2.40 USD (vs ~875 credits ≈ $11 for the full
stitch).

---

## Custom mix from the user

If the user overrides the recommendation, accept it but flag any structural
problems:

- No CTA at the end → ad has no call-to-action. Flag.
- Two of the same format back-to-back → repetitive, scroll-killing. Flag.
- Tutorial without UGC hook for cold traffic → no hook, won't stop the
  scroll. Flag.
- More than 5 clips → over-60s ads underperform on Reels/TikTok. Flag.

After flagging, defer to the user, their brand, their call. Log the
override in `01-format-list.md`.

---

## Save the format list

Write `<output>/01-format-list.md`:

```markdown
# Format Mix

**Goal:** <goal>
**Tier:** <cheap_test | full_stitch>

| # | Format | Duration | Role | File output |
|---|--------|----------|------|-------------|
| 1 | UGC | 15s | hook | clip-1-ugc.mp4 |
| 2 | Tutorial | 15s | demonstrate | clip-2-tutorial.mp4 |
| 3 | Unboxing | 10s | proof | clip-3-unboxing.mp4 |
| 4 | Product Review | 15s | social proof | clip-4-review.mp4 |
| 5 | CTA | 5s | action | clip-cta.mp4 |

**Total stitched duration:** <Ns>
**Avatar locked for clips 1, 2, 4 (Unboxing is hands-only, CTA is separate prompt):** <avatar name>
**Estimated credits:** <n>
```

---

## Output

- `<output>/01-format-list.md`

Proceed to `prompts/04-avatar-strategy.md` (if avatar isn't already
decided), then `prompts/03-multi-format-stitch.md` for the renders.
