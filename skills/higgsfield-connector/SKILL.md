---
name: higgsfield-connector
description: "Fully autonomous Higgsfield AI connector for Claude Code. Adds the official Higgsfield remote MCP server (https://mcp.higgsfield.ai/mcp), drives the OAuth sign-in once, verifies the connection, then loads the bundled Higgsfield prompt cookbook + Selr AI templates. The user's only action is signing in to their Higgsfield account once. Zero copy-paste, zero env vars, zero typing. Use when the user says 'connect Higgsfield', 'set up Higgsfield', 'install the Higgsfield kit', 'help me make AI ads', or 'I want to generate images and videos'."
allowed-tools: Bash, Read, Write, Edit
metadata:
  category: Creative & AI Generation
  tags: [higgsfield, image, video, soul-id, mcp, ads, oauth, autonomous]
  audience: non-technical business owner
  time-to-complete: 5 minutes
  cost-to-user: Higgsfield's standard plan pricing (paid to Higgsfield, free tier available for testing)
  autonomy-bar: "User signs in to Higgsfield once. Agent does everything else."
---

# Higgsfield Connector — Fully Autonomous OAuth Install

> **The standard**: the user signs in to Higgsfield once. Everything else is the agent.
>
> **No API keys.** No environment variables. No copy-paste. No JSON config edits.
>
> Auth is OAuth via the official remote MCP server at `https://mcp.higgsfield.ai/mcp`. One browser sign-in, then the agent verifies and loads templates.

---

## Autonomy Bar

| User DOES | User DOES NOT |
|---|---|
| Sign in to higgsfield.ai when the OAuth window opens (email or Google, ~30 sec) | Run any CLI command |
| Confirm in chat (max one yes/no) | Edit any config file |
| Restart Claude Code once | Copy or paste any token |
|  | Read any error message |

If at any point the agent is about to ask the user to copy or paste a value, **stop**. There are no values to copy in this flow.

---

## How This Skill Works

User says any of:
- "Connect Higgsfield"
- "Set up Higgsfield"
- "Install the Higgsfield kit"
- "Help me make AI ads / images / videos"
- "I want to generate cinematic videos"

Agent runs Phases 0..6. The user has exactly two touchpoints: the safety gate (one yes/no) and the OAuth sign-in window. That's the whole flow.

---

## Phase 0: Pre-Flight Checks (silent, mandatory)

Run these before sending a single message. Fix silently where possible.

```bash
# 1. Claude Code is installed
which claude || { echo "FAIL: Claude Code not found"; exit 1; }

# 2. Detect existing config — skip reinstall if already wired
EXISTING=$(claude mcp list 2>/dev/null | grep -i '^higgsfield')
if [ -n "$EXISTING" ]; then
  echo "ALREADY_CONFIGURED — skip to Phase 5 verify"
fi

# 3. ~/.claude/skills/ exists
mkdir -p "$HOME/.claude/skills"
```

If `claude mcp` is not available (very old Claude Code build), the agent says: *"I need a more recent Claude Code to add this connection. Update from claude.ai/download and try again."*

---

## Phase 1: Safety Gate (one short message)

Send ONE message. Wait for a single yes/no.

> **"Quick heads-up before I connect Higgsfield to your Claude Code:**
>
> - **What you'll get:** image + video generation across 30+ models — Soul, Sora 2, Veo 3.1, Kling, Seedance, Nano Banana, Cinema Studio. Plus a prompt cookbook and 15 ready-made templates.
> - **What you'll do:** sign in to higgsfield.ai once when a browser window opens. That's it.
> - **Cost:** Higgsfield has a free tier for testing. Paid plans only kick in if you upgrade — your call, paid to them, not us.
>
> **Ready? Say 'go' and I'll connect it."**

| User says | Agent does |
|---|---|
| 'go' / 'yes' / 'do it' / similar | Proceed to Phase 2 |
| 'no' / 'wait' / questions | Answer calmly. Wait for explicit consent. Do not pressure. |
| 'I don't have an account' | *"No problem — when the sign-in window opens, click 'Sign up'. Takes 30 seconds with Google."* Then proceed. |

---

## Phase 2: Add the MCP Server (one CLI call, agent runs it)

Run silently:

```bash
claude mcp add --transport http higgsfield https://mcp.higgsfield.ai/mcp --scope user
```

Why `--scope user`: the connection persists across all of the user's projects, not just the current folder.

If the command errors, retry once with `--scope local`. If still fails, surface the error in plain English (translate `EADDRINUSE`, `ENOTFOUND`, etc. — never dump raw text).

---

## Phase 3: OAuth Sign-In (the only user moment)

Right after `claude mcp add` runs, the server's status will read **"Needs authentication"**. That's expected — Claude Code will trigger an OAuth browser flow the next time the user (or you) actually invokes a Higgsfield tool.

Tell the user:

> **"Adding it now. In a moment a browser window will open asking you to sign in to Higgsfield — use Google for the fastest path. When you see 'Connection successful' in the browser, come back and tell me 'done'."**

Verify the registration, then trigger OAuth by asking Claude Code (in this session) to use any Higgsfield tool:

```bash
claude mcp get higgsfield
```

If `Status: ! Needs authentication`, ask Claude Code in this session something like *"list the available Higgsfield models"*. The first tool call from the user's Claude Code (the same session, or a new one if the agent is running headless) will open the OAuth window.

If the browser window doesn't open after 30 seconds, ask the user to fully quit and reopen Claude Code, then ask the same question again — some Claude Code builds need a fresh launch to register the new HTTP MCP.

Wait for the user to confirm they're signed in.

---

## Phase 4: Restart Claude Code (only if needed)

Most builds pick up the new MCP without restart. Some require it. Verify the entry is registered:

```bash
claude mcp get higgsfield
```

Expected: `Status: ! Needs authentication` (the OAuth handshake hasn't fired yet — that's fine until Phase 5).

If `claude mcp get higgsfield` errors with "MCP server not found":

> **"One last step — fully quit Claude Code (Cmd+Q on Mac, close window AND tray icon on Windows) and reopen it. Tell me when you're back."**

If the tool IS discoverable, skip this phase entirely.

---

## Phase 5: Live Verification (silent)

Confirm the MCP is fully wired. The exact tool name surface for Higgsfield's remote MCP is discovered at runtime — once OAuth completes, Claude Code exposes tools as `mcp__higgsfield__<name>`. Don't hardcode tool names; instead, verify by listing what's available.

```bash
claude mcp get higgsfield   # status should be "Connected", not "Needs authentication"
```

Then ask Claude Code (in the user's session) something simple to exercise the connection:

> *"Use Higgsfield to list the models you can access."*

| Outcome | Action |
|---|---|
| Claude lists Higgsfield models (Soul, Sora, Kling, Veo, etc.) | Success. Proceed to Phase 6. |
| `Status: Needs authentication` | OAuth didn't complete. Re-run Phase 3. |
| `Status: Failed to connect` | URL or network issue. Re-run `claude mcp add` and check that the URL ends in `/mcp`. |
| Tool list empty | OAuth completed but no scopes granted — ask user to revoke + re-authorise from higgsfield.ai → Settings → Connected apps. |

Capture the returned model list — surface a few model names in Phase 6 to prove the connection is real.

---

## Phase 6: Hand-Off (warm, useful, three starter prompts)

Send the user one final message. Match the prompts to whatever business they mentioned earlier in the conversation if possible.

> **"Done — you're connected to Higgsfield. Try one of these to start:**
>
> 1. *'Generate a cinematic founder portrait for me using the Selr AI template.'* → uses `templates/selrai-founder-portrait.md`
> 2. *'Make me an 8-second ASMR scroll-stopper video for a [your product].'* → uses `templates/selrai-asmr-scroll-stopper.md`
> 3. *'Show me the Soul ID workflow so I can train my own avatar.'* → opens `docs/soul-id-workflow.md`
>
> **All 15 templates are in `~/Higgsfield-Creative-Kit/templates/`. Full prompt cookbook is in `docs/cookbook.md`.**
>
> When you want a prompt rewritten, polished, or adapted to a new model — just ask. I'll use the bundled prompt skill to handle it."

---

## Skill Behaviour After Setup

These rules govern future conversations once Higgsfield is connected.

### Always pass through the prompt skill first
When the user asks for a Higgsfield prompt, read `~/.claude/skills/higgsfield/SKILL.md` and route to the right sub-skill (camera, motion, soul, cinema, seedance, etc.) before calling the MCP. The vendored prompt skill has 20 sub-skills + 10 genre templates — use them.

### MCSLA formula for every video prompt
Model · Camera · Subject · Look · Action. If the user gives you fewer than 4 of these, ask for the missing one or fill it from context.

### Lock seeds for series
When the user asks for "more like that" or a variation, reuse the seed from the prior generation and change only one variable.

### Soul ID workflow
For character-consistent output, route through `docs/soul-id-workflow.md`. The vendored `higgsfield-soul` sub-skill handles the prompting; the doc handles training.

### Never echo credentials
The OAuth tokens never appear in any user-visible output.

### Cost awareness
If the user is on the free tier and asks for a heavy job (10+ video generations, 4K upscales), warn once before running.

---

## Troubleshooting Matrix

| Symptom | Diagnosis | Fix |
|---|---|---|
| `claude mcp add` errors with `command not found` | Old Claude Code build | *"Update Claude Code from claude.ai/download and try again."* |
| OAuth window doesn't open | Claude Code waiting for first tool call to trigger it | Ask Claude in the user's session to "list Higgsfield models" — the first tool call triggers OAuth |
| 401 on first tool call | OAuth didn't complete | Re-run sign-in. Browser may have blocked the popup. |
| Tool not discoverable after restart | MCP entry didn't save | Re-run `claude mcp add --transport http higgsfield https://mcp.higgsfield.ai/mcp --scope user` |
| All generations return "rate limited" | Free tier exhausted | *"You've hit your free-tier cap. Higgsfield's billing page handles upgrades — I'll pause here."* |
| Sora 2 / Veo 3 returns "model unavailable" | Plan tier doesn't include premium models | *"That model is on Higgsfield's higher plan. Want me to fall back to Kling or Seedance?"* |

---

## Setup Checklist (agent tracks)

Do NOT tell the user "done" until every box is ticked:

- [ ] Phase 0: Claude Code present, no existing higgsfield MCP entry (or skipped to verify)
- [ ] Phase 1: user said go
- [ ] Phase 2: `claude mcp add` exited 0
- [ ] Phase 3: user confirmed OAuth sign-in
- [ ] Phase 4: `claude mcp get higgsfield` shows `Status: Connected` (restart Claude Code if needed)
- [ ] Phase 5: live `list_models` returned a non-empty model list
- [ ] Phase 6: three starter prompts matched to user's business sent

---

## Reference

- **Official MCP server**: `https://mcp.higgsfield.ai/mcp`
- **Higgsfield platform**: [higgsfield.ai](https://higgsfield.ai)
- **MCP docs**: [higgsfield.ai/mcp](https://higgsfield.ai/mcp)
- **Bundled prompt skill**: `~/.claude/skills/higgsfield/` (vendored from OSideMedia, MIT)
- **Templates**: `~/Higgsfield-Creative-Kit/templates/`
- **Cookbook**: `~/Higgsfield-Creative-Kit/docs/cookbook.md`
- **Soul ID workflow**: `~/Higgsfield-Creative-Kit/docs/soul-id-workflow.md`
- **Pairing with other skills**: `~/Higgsfield-Creative-Kit/docs/pairing-with-other-skills.md`

---

*Built by Selr AI. If Higgsfield's MCP changes and this flow breaks, email support@selrgroup.com.au.*
