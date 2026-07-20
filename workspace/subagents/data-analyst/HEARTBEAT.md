# HEARTBEAT.md  (Prism — proactive loop; ships OFF)

This agent's heartbeat is disabled by default (openclaw.json → agents.list[] → "data-analyst" →
heartbeat.every: "0m"). Enable it by setting a real interval (e.g. "30m") — the BOOTSTRAP setup
offers this. Until then, these checks run only when you're spawned and asked.

## Every tick (when enabled)
1. Scan the latest dump for anomalies in signups/usage worth surfacing; silence if nothing moved.
2. Anything worth the team's attention → report it to the main agent. Default outcome of a
   tick is silence.
