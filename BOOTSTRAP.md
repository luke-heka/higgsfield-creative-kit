# Higgsfield Creative Kit — paste-into-Claude prompt

Copy the entire code block below and paste it into a fresh Claude Code session.
Claude does the rest. You only sign in to Higgsfield once when a browser window opens.

````
You are about to install the Higgsfield Creative Kit for me. Do these steps in order, autonomously, without asking me to do anything except sign in to Higgsfield once when prompted.

1. Detect my OS. If Mac/Linux, use bash. If Windows, use powershell.

2. Find the kit. Look in this order, take the first that matches:
   a. `~/Downloads/higgsfield-creative-kit*.zip` (or `.tar.gz`)
   b. `~/Desktop/higgsfield-creative-kit*.zip`
   c. Any folder already named `higgsfield-creative-kit` in `~/Downloads/` or `~/Desktop/`
   d. If none found, clone fresh: `git clone https://github.com/lukeselr/higgsfield-creative-kit /tmp/higgsfield-creative-kit`

3. If you found a zip/tar, extract it to `/tmp/higgsfield-creative-kit/`.

4. Run the installer:
   - Mac/Linux: `bash /tmp/higgsfield-creative-kit/install.sh`
   - Windows: `powershell -File "C:\path\to\install.ps1"`

5. Run the smoke test: `bash /tmp/higgsfield-creative-kit/smoke-test.sh`. Confirm every line says `ok`.

6. Now invoke the connector skill. Read `~/.claude/skills/higgsfield-connector/SKILL.md` and execute Phases 0..6 verbatim. The skill will:
   - Run `claude mcp add --transport http higgsfield https://mcp.higgsfield.ai/mcp --scope user`
   - Open a browser for me to sign in to Higgsfield once (Google sign-in is fastest)
   - Verify the MCP is live by listing models
   - Hand off three starter prompts matched to my business

7. After verification, briefly summarise what's now installed: connector skill, prompt skill, 15 templates, cookbook, Soul ID workflow.

8. Ask me what I want to make first. Suggest one image and one video starter from `~/Higgsfield-Creative-Kit/templates/`.

Do not ask me yes/no questions about steps 1-7 — just do them. The only place you wait for me is the browser sign-in moment in step 6 and my final answer in step 8.
````

After Claude finishes, you'll have:

- The Higgsfield MCP wired into Claude Code (no API keys, OAuth only).
- A vendored prompt cookbook with 20 sub-skills (Soul ID, Cinema Studio, Seedance, Kling Motion Control, etc.).
- 15 ready-made templates — 8 image, 7 video — tuned for founder content.
- A full Soul ID training workflow doc.
- Pairing guides for combining Higgsfield with carousel-generator, copywriting, and ad-creative skills.

If anything breaks, email `support@selrgroup.com.au`.
