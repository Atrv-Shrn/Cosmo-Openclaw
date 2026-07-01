---
name: "proposals"
description: "Manage the proposals ledger (PROPOSALS.md) — check before raising something, log it OPEN, mark it DONE when resolved or rejected. So you never raise the same thing twice."
---

# proposals

The proposals ledger is PROPOSALS.md — a human-reviewable list of things worth a human's
attention. This skill is the *how*; PROPOSALS.md is just the data.

## Before raising anything
- Read PROPOSALS.md first. If the same (or a near-identical) item is already under `## Open`, do
  nothing — never raise the same thing twice. If it's under `## Resolved` and has genuinely come
  back, you may re-open it with a fresh dated line.

## To log a new item
- Add ONE line under `## Open`:  `OPEN <short description> (YYYY-MM-DD)`
- One concern per line. Keep it to a single line.

## To close an item
- When it's resolved, accepted, or rejected, move its line to `## Resolved`, change `OPEN` → `DONE`,
  and add a few words on the outcome:  `DONE <short description> — accepted (YYYY-MM-DD)`

## Rules
- One line per entry, always dated.
- PROPOSALS.md holds data only — no prose, no logic (that lives here).
- Dreaming does NOT tidy PROPOSALS.md. It's managed only by this skill.
