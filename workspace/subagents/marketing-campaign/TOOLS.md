# TOOLS.md — Local Notes (Nova)

Environment notes specific to this specialist. Keep it short; update as you learn.

## Environment
- Workspace: ~/.openclaw/workspace/subagents/marketing-campaign (this folder).
- Shared context in the main workspace (~/.openclaw/workspace): repos/ (code, read-only for you),
  db/ (disposable data dump), .env (secrets — read at runtime, never echo).

## Where the tools are
- MCP servers: openclaw.json (`mcp.servers`) is the source of truth. Recommended for this role:
  LinkedIn / X, Canva (see the project README — install your own).
- Skills: common skills are shared from the main workspace/skills/; your specialized ones live
  in skills/ here (yours win on a name clash).
- The rule that never changes: repo/project code is edited only by the main agent's Claude Code
  sub-agent — never by you.
