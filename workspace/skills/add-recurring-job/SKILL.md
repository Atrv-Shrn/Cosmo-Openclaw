---
name: "add-recurring-job"
description: "Set up a recurring or scheduled job. Use when asked for a repeating check, a cron job, a daily/weekly task, or 'something that runs on a schedule'. Picks heartbeat vs cron and edits the right files itself."
---

# add-recurring-job

One entry point for "I need a recurring job." You decide the mechanism, then wire it yourself.

The two mechanisms: the **heartbeat** (one loop in HEARTBEAT.md, fires many times a day) and
**OpenClaw cron** (scheduled jobs held in the gateway, once a day / at a set time). This skill owns
that distinction — HEARTBEAT.md itself stays about ticks only.

## Pick the mechanism
- Runs MANY times a day (monitoring, awareness sweeps — anything that just needs to happen often
  and can be approximate) → a HEARTBEAT tick.
- Runs ONCE a day, or at a specific clock time (digests, a 9am summary, a weekly review) → an
  OpenClaw cron job.

Rule of thumb: many-times-a-day → heartbeat; once-a-day-or-scheduled → cron. Don't create several
cron jobs that fire on the same interval — batch those into one heartbeat tick instead.

## Heartbeat path (recurs many times a day)
1. If the check is non-trivial, write skills/<name>/SKILL.md for it first (copy the shape of an
   existing skill, or follow skills/script).
2. Add a numbered step under "## Every tick" in HEARTBEAT.md that runs it. Keep silence the
   default.
3. No config change — the heartbeat already fires on its `every` interval (openclaw.json).

## Cron path (once a day / set time)
1. If the job is non-trivial, write skills/<name>/SKILL.md for it first.
2. Create the job on the box:
   `openclaw cron add --name "<name>" --cron "<expr>" --tz <TIMEZONE> --session isolated --message "<what to do, e.g. run skills/<name>>" --announce`
   - `<expr>` is a 5-field cron string: `"0 5 * * *"` = 05:00 daily, `"0 9 * * 1"` = 09:00 Mondays.
   - `--session isolated` gives a fresh, context-light run. Drop `--announce` if it should stay
     quiet unless it has something to say.
3. Done — the job lives in the gateway, not in any workspace file. `openclaw cron list` is the
   source of truth for what's scheduled. Never copy cron jobs into HEARTBEAT.md (that file is for
   heartbeat ticks only).

## Verify
- Cron: `openclaw cron list` shows the job. Run `openclaw cron --help` first — flag names can vary
  by version, so adapt the command above to what your version accepts.
- Heartbeat: the new step appears under "## Every tick" and runs on the next tick.
