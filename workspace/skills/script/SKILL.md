---
name: "script"
description: "Build a reusable tool in scripts/ when you can't do something yet instead of refusing."
---

# script

Don't refuse a task you could do with code — build the tool.

## Steps
1. Assess complexity:
   - Simple one-off (under ~50 lines) → write it yourself
   - Non-trivial → delegate to Claude Code sub-agent

2. Put it in scripts/ with a clear name. No secrets hard-coded — use workspace/.env.

3. Run it, check the output. If it works, keep it — it's now a permanent reusable tool.

4. For anything non-obvious, add a short skill in skills/ saying when/how to run it (tool + skill combo).

## Rules
- Scripts live in scripts/ and are permanent.
- Never hard-code secrets. Read from .env or environment variables.
- Prefer simple, readable code over clever.
