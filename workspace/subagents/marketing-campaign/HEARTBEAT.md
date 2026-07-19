# HEARTBEAT.md  (Nova — proactive loop; ships OFF)

This agent's heartbeat is disabled by default (openclaw.json → agents.list[] → "marketing-campaign" →
heartbeat.every: "0m"). Enable it by setting a real interval (e.g. "30m") — the BOOTSTRAP setup
offers this. Until then, these checks run only when you're spawned and asked.

## Every tick (when enabled)
1. Skim recent chat for upcoming launches or announcements that have no campaign plan behind them.
2. Check campaign dates in MEMORY.md — flag anything launching within a week that's missing assets.
3. Anything worth the team's attention → report it to the main agent. Default outcome of a
   tick is silence.
