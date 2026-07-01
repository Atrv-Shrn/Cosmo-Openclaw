# scripts/ — the agent's permanent, self-built tools (procedural memory)

Starts empty. When the agent hits a task it can't do yet, it builds a tool here (via
`skills/script`) instead of refusing — permanent and reusable. Secrets are never hard-coded; they
come from `workspace/.env`.
