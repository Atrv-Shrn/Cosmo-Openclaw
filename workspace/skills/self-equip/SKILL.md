---
name: "self-equip"
description: "When stuck on something technical, search ClawHub for skills and GitHub for MCPs, then install the appropriate ones to continue."
---

# Self-Equip

When you hit a technical blocker, don't stop and ask the user for help immediately. Try to unblock yourself first.

## When to use
- A task requires a tool or capability you don't have
- You're missing an MCP server, CLI, or library that would let you proceed
- You're about to ask the user to do something you could probably automate

## Steps

1. **Search ClawHub for existing skills**
   - Run `openclaw skills search <keyword>` or check the OpenClaw skills marketplace
   - If a relevant skill exists, install it: `openclaw skills install <name>`
   - Read the skill file and follow it

2. **Search GitHub for MCPs**
   - Use `web_search` for `site:github.com mcp <keyword>` or `github.com/modelcontextprotocol <keyword>`
   - Check the MCP registry: https://github.com/modelcontextprotocol/servers
   - If found, install via `openclaw mcp add <name> --command npx --arg -y --arg <package>`
   - Probe to verify: `openclaw mcp probe <name>`

3. **Search Context7 for docs**
   - Use the Context7 MCP tools (resolve-library-id, query-docs) to find up-to-date documentation for the library/API you're working with

4. **If nothing found, build it yourself**
   - Follow `skills/script/SKILL.md` to create a reusable script
   - For non-trivial tools, delegate to a Claude Code sub-agent

5. **Only ask the user when genuinely blocked**
   - You need credentials, access, or a decision only they can make
   - The task requires external actions (payments, account creation, etc.)
   - You've searched and tried but nothing worked

## Rules
- Prefer installing over building. Prefer building over asking.
- Keep the user informed but don't wait for permission on reversible actions.
- Always probe/verify after installing an MCP server.
- Log what you installed in INSTRUCTIONS.md so future sessions know it's available.
