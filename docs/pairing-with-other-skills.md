# Pairing Higgsfield with Other Skills

Higgsfield is the **visuals layer**. To run the full creative loop, pair it
with sister skills that handle the layers around it: copy, layout, audio,
distribution, post.

This doc is about combinations — what to run before Higgsfield, what to run
after, what to run alongside.

## The full creative loop

```text
1. Strategy        →  ad-creative skill, content-marketer skill
2. Copy + hooks    →  copywriting, direct-response-copy, email-marketing
3. Visuals         →  Higgsfield (this kit)
4. Voice + audio   →  ElevenLabs, Higgsfield Speak, OpenAI TTS
5. Polish          →  nano-banana MCP (image), your editor (video)
6. Layout          →  carousel-generator, Figma, Canva
7. Distribution    →  meta-ads-mcp-setup, social-content, manychat
8. Post-clean      →  humanizer skill (any text that goes live)
```

Most operators try to do everything in one tool. The high-output operators
specialise each layer and chain them.

## Combinations that work

### Hero portrait series → IG carousel

```text
1. selrai-founder-portrait.md  → 5 portrait variations, locked seed
2. nano-banana MCP              → 4K upscale each
3. carousel-generator skill     → 5-slide branded carousel
4. copywriting skill            → caption + hook + CTA
5. humanizer skill              → strip AI tone from caption
6. social-content skill         → schedule across IG + LinkedIn
```

### Product launch — full ad set

```text
1. selrai-product-hero.md           → 4 hero shots, locked seed
2. selrai-asmr-scroll-stopper.md    → 3 ASMR variants
3. selrai-ugc-talking-head.md       → 5 UGC variants with hook A/B/C
4. ad-creative skill                → critique each variant, pick winners
5. direct-response-copy skill       → primary text + headline + CTA
6. meta-ads-mcp-setup               → upload to Meta as new ad set
7. paid-ads skill                   → set bidding, audiences, exclusions
```

### Founder-led brand film

```text
1. Train a Soul ID                  → docs/soul-id-workflow.md
2. selrai-cinema-studio-narrative.md → 5 narrative shots, varied moves
3. selrai-lifestyle-broll.md        → 8 b-roll moments
4. ElevenLabs / Higgsfield Speak    → voiceover script delivery
5. Your editor (Premiere, Final Cut)→ stitch + sound design
6. social-content skill             → multi-platform cut-down + caption
```

### UGC ad volume engine

```text
1. selrai-ugc-talking-head.md       → 1 winning visual base
2. direct-response-copy skill       → 20 hook variations
3. selrai-recast-character-swap.md  → recast each hook into the visual base
4. meta-ads-mcp-setup               → upload all 20 as separate creatives
5. ad-creative skill                → after 48hr, kill bottom 50%, scale top 3
```

### Trend-jacking, fast

```text
1. last30days skill                 → find the trending format this week
2. selrai-sora2-trend-template.md   → drop your brand into the trend
3. social-content skill             → caption tuned to the platform
4. humanizer skill                  → final pass on caption
```

## Sister skills, one-liner each

| Skill | What it does | Lives at |
|---|---|---|
| **nano-banana MCP** | 4K image upscale + edit | Already in your MCP stack |
| **carousel-generator** | Render branded IG carousels from images | `~/.claude/skills/carousel-generator/` |
| **copywriting** | Long-form copy: pages, emails, scripts | `~/.claude/skills/copywriting/` |
| **direct-response-copy** | Hooks, headlines, CTAs, ad copy | `~/.claude/skills/direct-response-copy/` |
| **email-marketing** | HTML emails + sequences for GHL | `~/.claude/skills/email-marketing/` |
| **email-sequence** | Drip-campaign + lifecycle email programs | `~/.claude/skills/email-sequence/` |
| **ad-creative** | Full ad system: visual + copy + landing | `~/.claude/skills/ad-creative/` |
| **paid-ads** | Campaign strategy + bidding across platforms | `~/.claude/skills/paid-ads/` |
| **meta-ads-mcp-setup** | Connect Meta Ads to Claude Code | Sister kit at `github.com/lukeselr/meta-ads-mcp-setup` (separate one-prompt install, not bundled here) |
| **social-content** | Multi-platform scheduling + optimisation | `~/.claude/skills/social-content/` |
| **humanizer** | Strip AI tone from any text | `~/.claude/skills/humanizer/` |
| **avoid-ai-writing** | Audit text for AI-pattern signatures | `~/.claude/skills/avoid-ai-writing/` |
| **last30days** | Trending content / formats this week | `~/.claude/skills/last30days/` |
| **content-creator** | SEO-optimised content with brand voice | `~/.claude/skills/content-creator/` |
| **content-marketer** | AI-powered content + omnichannel distribution | `~/.claude/skills/content-marketer/` |

## Anti-patterns

- **Don't ask Higgsfield to write copy.** It's a visuals tool. Use a copy
  skill, paste the result back into your Higgsfield prompt as the dialogue
  field.
- **Don't ask a copy skill to choose visuals.** Inverse problem — let each
  skill specialise.
- **Don't skip the humanizer pass.** Anything text-shaped that ends up in
  front of your audience should pass through `humanizer` or `avoid-ai-writing`
  before publishing.
- **Don't let Click-to-Ad be your hero piece.** It's a volume tool. For brand
  hero spots, build deliberately with `selrai-cinema-studio-narrative.md`.
- **Don't run Recast on someone you don't have rights to.** Hard ethical line.
  See `docs/soul-id-workflow.md` § "Ethical guardrails".

## When in doubt

If you're not sure which skill to pair with a Higgsfield output, the answer
is almost always: **`humanizer` on the caption, `nano-banana` on the image,
your editor on the video, `meta-ads-mcp-setup` for distribution.**

That's the four-skill spine of every shipped piece.
