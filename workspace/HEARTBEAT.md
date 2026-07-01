# HEARTBEAT.md  (proactive loop; you may edit this; add items over time)

## Settings (edit these)
- Timezone: <TIMEZONE>
- Quiet hours: 11:00 pm to 5:00 AM
  During quiet hours, only an urgent alert may interrupt. Everything else waits.

How often this loop fires, and whether it runs at all at a given hour, are set in
openclaw.json (heartbeat `every` + `activeHours`). Default outcome of every tick is silence.

## Every tick
1. Skim recent chat for loose ends (unanswered questions, ambiguous decisions, follow-ups) and
   repeated tasks (offer to build a tool/skill for them).
2. Anything that clears THE BAR → run skills/proposals to log it (it dedupes and adds the OPEN line).

## THE BAR
Actionable, not already raised, worth a human's attention.

## Adding a check
To add a recurring check (site health, a daily digest, a sync job, …), run
skills/add-recurring-job. It picks the mechanism (a tick here, or an OpenClaw cron job) and wires
it in for you. Keep silence the default.
