# HEARTBEAT.md  (Atlas — proactive loop; ships OFF)

This agent's heartbeat is disabled by default (openclaw.json → agents.list[] → "investor-relations" →
heartbeat.every: "0m"). Enable it by setting a real interval (e.g. "30m") — the BOOTSTRAP setup
offers this. Until then, these checks run only when you're spawned and asked.

## Every tick (when enabled)
1. Check the date — if a monthly investor update window is near and no draft exists, flag it.
2. Anything worth the team's attention → report it to the main agent. Default outcome of a
   tick is silence.
