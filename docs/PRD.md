# PRD — Cosmo-Openclaw (living state)

Terse, high-signal record of decisions, milestones, and what's next. Code/git history covers the rest.

## What this project is

The generalized, shareable OpenClaw config for **Cosmo** — a self-evolving startup ops agent
(Telegram-resident, heartbeat-driven, delegates all repo/project code to a Claude Code sub-agent).
Everything personal/secret is a `<PLACEHOLDER>`; real secrets only in git-ignored `workspace/.env`.

## Current state

- **v1.1.0 built (2026-07-19)** on branch `sub-agents` — awaiting user review/merge decision.
  `main` untouched (never merge/push without explicit instruction).
- Spec: `docs/SPEC-v1.1.0.md` (status: implemented). Full system spec: `docs/SPEC.md`
  (git-ignored, local-only, regenerated with the roster).

## v1.1.0 — sub-agent roster (implemented)

- 11 complete specialists in `workspace/subagents/<name>/`, each with 8 md files
  ({AGENTS,SOUL,IDENTITY,USER,INSTRUCTIONS,MEMORY,HEARTBEAT,TOOLS}.md) + own `skills/` (empty,
  `.gitkeep`). Pre-named identities (Nova, Quill, Scout, Atlas, Sentinel, Ledger, Magnet, Patch,
  Radar, Prism, Wrench).
- Registered in `openclaw.json`: `agents.list[]` = main (`id: "main"`, `default: true`, explicit
  heartbeat) + 11 specialists; `subagents{}` allow-list lives **on the main entry**
  (maxConcurrent 3, maxSpawnDepth 1, archiveAfterMinutes 60); shared skills via
  `skills.load.extraDirs` → `workspace/skills/`.
- **Doc-verified deviations from the draft spec** (OpenClaw docs checked at build, per locked
  decision): heartbeats disable with `every: "0m"` (no `enabled` key exists); `subagents{}` is
  per-agent, not top-level; `agents.defaults.skills` / `agents.list[].skills` are restrictive
  allowlists, so they're **omitted** and the shared root uses `skills.load.extraDirs` instead;
  main agent registered explicitly because "when any agent defines heartbeat, only those agents
  run heartbeats".
- All specialist heartbeats ship OFF; BOOTSTRAP Phase 3 flips `heartbeat.every` per chosen agent.
- `BOOTSTRAP.md` = self-contained installer + tutorial (primer, 12-placeholder table, identity,
  specialist/heartbeat picks, capability tutorial, MCP pointer, verify → delete).
- One root README only; per-folder READMEs in `db/`, `repos/`, `scripts/` replaced with `.gitkeep`
  (+ `.gitignore` whitelist updated). `<VERCEL_PROJECT>` removed; README gained a
  Recommended-MCP-servers table (project ships no MCPs).
- Boundary rules: specialists never edit repo code, never spawn Claude Code (main owns that path),
  never spawn each other; devops runs commands + small glue scripts only; specialists may read the
  shared `.env`.
- Sub-agent sessions auto-inject only AGENTS.md + TOOLS.md → each specialist's AGENTS.md has an
  "On wake" rule to read its IDENTITY/SOUL/INSTRUCTIONS/MEMORY.

## Key decisions (with why)

- **Spawn by registered id + AGENTS.md re-steers every delegation** — OpenClaw tends to ignore
  registered agents even when configured.
- **Complete agents, not thin briefs** — faithful to OpenClaw's file-driven model.
- **Hybrid skills** (shared root + per-agent folder) — zero duplication, workspace wins on clash.
- **Ship-off heartbeats, opt-in via BOOTSTRAP** — dormant by default.
- **No MCPs/plugins/vendor config in the repo** — recommend-only (README table); a bad MCP can
  crash the gateway.
- **Proposals for specialists are user-wired on request**, not shipped.

## Next

- User review of the `sub-agents` branch; merge only on explicit instruction.
- Optional/deferred: RAG pipelines, avatar, per-specialist proposals ledgers (on request),
  infra-specific skills stay out of the generalized config.
