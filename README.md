# Higgsfield Creative Kit

**One prompt. Connect Higgsfield to Claude Code. Generate cinematic images and videos with founder-grade templates.**

Built by Selr AI for non-technical founders. Zero API keys. One browser sign-in.

## What's in here

- **Connector skill** — autonomous OAuth installer for the official Higgsfield remote MCP at `https://mcp.higgsfield.ai/mcp`. Adds the connection, verifies it, hands off starter prompts.
- **Prompt skill** — vendored from [OSideMedia/higgsfield-ai-prompt-skill](https://github.com/OSideMedia/higgsfield-ai-prompt-skill) under MIT. 20 sub-skills covering Soul ID, Cinema Studio 2.5/3.0/3.5, Seedance 2.0, Kling 3.0 Motion Control, MCSLA formula, and 10 genre templates.
- **15 founder templates** — 8 image + 7 video, tuned for product, lifestyle, UGC, and ad use cases.
- **Soul ID workflow doc** — train a consistent character once, generate dozens of on-brand visuals.
- **Cookbook** — distilled prompting playbook: image formula, motion formula, the seven hard rules, locked seeds, real-gear references.
- **Full toolkit map** — every Higgsfield surface you can use: MCP tools, the 50+ one-click Apps, Cinema Studio, Lipsync Studio, Sketch-to-Video, Higgsfield Speak, Higgsfield Assist (GPT-5 copilot), the Chrome extension, and the mobile app.
- **Getting-started playbook** — first 30 minutes: confirm install, train Soul ID, ship your first image, ship your first video.
- **Pairing guide** — how to combine Higgsfield outputs with carousel generators, copywriting skills, and ad-creative workflows.

## Install

Open Claude Code and paste the prompt from [`BOOTSTRAP.md`](BOOTSTRAP.md). Claude does everything except your one Higgsfield sign-in.

## What you can do after install

- *"Generate a cinematic founder portrait of me holding [my product]"* → `templates/selrai-founder-portrait.md`
- *"Make me an 8-second ASMR scroll-stopper for [my product]"* → `templates/selrai-asmr-scroll-stopper.md`
- *"Create a UGC talking-head ad for [my product] using my Soul ID"* → `templates/selrai-ugc-talking-head.md`
- *"Show me three product hero shots, locked seed, three lighting variants"* → `templates/selrai-product-hero.md`
- *"Train my Soul ID — walk me through it"* → `docs/soul-id-workflow.md`

## What's NOT in here

- **No API keys.** The kit uses OAuth via Higgsfield's official remote MCP — your credentials live on Higgsfield, not in any config file on your machine.
- **No video editing.** Higgsfield generates clips. For stitching, captioning, or final cut, pair with Remotion or your editor of choice.
- **No copywriting.** Pair with Claude's `copywriting` or `direct-response-copy` skills to write the captions and hooks that go with your visuals.
- **No paid ads.** Pair with `paid-ads`, `ad-creative`, or `meta-ads-mcp-setup` for actual campaign launch.

## Files

```text
higgsfield-creative-kit/
  BOOTSTRAP.md                        # paste-into-Claude install prompt
  README.md                           # this file
  PROMPTS.md                          # quick-reference starter prompts
  NOTICE                              # MIT attribution for OSideMedia
  install.sh / install.ps1            # OS-detected installer
  smoke-test.sh                       # post-install verification
  skills/
    higgsfield-connector/             # autonomous OAuth installer (Selr AI)
    higgsfield/                       # vendored prompt skill (OSideMedia, MIT)
  templates/
    selrai-founder-portrait.md        # image
    selrai-product-hero.md            # image
    selrai-lifestyle-broll.md         # image
    selrai-social-carousel-cover.md   # image
    selrai-behind-the-scenes.md       # image
    selrai-founder-with-product.md    # image
    selrai-before-after-pair.md       # image
    selrai-team-group-shot.md         # image
    selrai-ugc-talking-head.md        # video
    selrai-asmr-scroll-stopper.md     # video
    selrai-click-to-ad-product.md     # video
    selrai-sora2-trend-template.md    # video
    selrai-cinema-studio-narrative.md # video
    selrai-draw-to-video-product.md   # video
    selrai-recast-character-swap.md   # video
  docs/
    getting-started.md                # first 30 minutes after install
    cookbook.md                       # prompting playbook
    soul-id-workflow.md               # train your character once
    full-toolkit-map.md               # every Higgsfield surface
    pairing-with-other-skills.md      # combine with sister skills
```

## Pairing this kit with other skills

This kit is the visuals layer. To run the full creative loop, pair with:

| When you want | Pair with |
|---|---|
| 4K image polish on Higgsfield outputs | `nano-banana` MCP |
| Multi-slide branded carousel from generated images | `carousel-generator` skill |
| Caption + hook copy for the visuals | `copywriting` or `direct-response-copy` skill |
| End-to-end ad system (creative + targeting + landing) | `ad-creative` skill |
| Launch campaigns to Meta from generated assets | `meta-ads-mcp-setup` |
| Strip AI tone from any pasted captions | `humanizer` skill |

See [`docs/pairing-with-other-skills.md`](docs/pairing-with-other-skills.md) for worked examples.

## Support

If install breaks, email `support@selrgroup.com.au`. Built for the Selr AI workshop community.

---

- Instagram: [@mr_heka](https://instagram.com/mr_heka), [@selr__ai](https://instagram.com/selr__ai)
- YouTube: [@mr_heka](https://youtube.com/@mr_heka)
- Workshop: [workshop.selrai.com.au](https://workshop.selrai.com.au)
