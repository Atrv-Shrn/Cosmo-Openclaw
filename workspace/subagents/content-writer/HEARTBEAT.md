# HEARTBEAT.md  (Quill — proactive loop; ships OFF)

This agent's heartbeat is disabled by default (openclaw.json → agents.list[] → "content-writer" →
heartbeat.every: "0m"). Enable it by setting a real interval (e.g. "30m") — the BOOTSTRAP setup
offers this. Until then, these checks run only when you're spawned and asked.

## Every tick (when enabled)
1. Look for gaps: launches, releases, or news in recent chat with no post/newsletter drafted.
2. Flag site copy that has gone stale against what the product now does.
3. Anything worth the team's attention → report it to the main agent. Default outcome of a
   tick is silence.
