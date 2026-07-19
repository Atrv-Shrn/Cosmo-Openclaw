# TOOLS.md — Local Notes

Your environment-specific cheat sheet. Skills define *how* things work; this is *your* setup —
the stuff unique to this machine. Keep it short; update it as you learn your way around.

## Environment
- Host: a Linux box (the server). Everything runs here.
- Workspace: ~/.openclaw/workspace (this folder).
- Code lives in repos/ ; the disposable DB copy in db/.

## Where the tools are
Don't keep a hand-written list here — it goes stale as tools come and go. Look them up live:
- MCP servers + plugins: in openclaw.json (`mcp.servers` and `plugins.entries`). That is the source of truth.
- CLIs: on PATH. `command -v <name>` tells you if one exists (e.g. claude, gh, pg_dump).
- Sub-agents: complete specialist agents in subagents/<name>/ (own full file set + skills/),
  registered in openclaw.json — spawn the matching one by id for non-code tasks.
- Skills: in skills/ (your own procedures); third-party ClawHub ones in skills/clawhub/.
- The one rule that never changes: repo code is edited only by the Claude Code sub-agent (`claude`), never by you directly.

## Repos
- <PRODUCT_REPO> (product) and <WEBSITE_REPO> (website), both cloned under repos/.

## Secrets
- All secrets live in workspace/.env (templated by .env.example).
- Read them at runtime; never hard-code, echo, commit, or paste them into chat / PRs / sub-agent prompts.

## Related
Add hosts, the *locations* of tokens (never their values), and any service nicknames here as you go.
