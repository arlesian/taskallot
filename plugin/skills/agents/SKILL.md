# Inspect agents

`/agents` is a working product name. [Integration](../../../controller/codex-integration.md) owns invocation and host-discovery questions.

This skill reads controller state and events. It shows current and recent agents using the [monitor fields](../../../interface/terminal-monitor.md) and [shared vocabulary](../../../controller/task-assessment.md).

Group agents by task, run, and manager. Support filters and inspection of one agent or assignment. Include artifact references, reporting state, checked revisions, and blockers when relevant.

Use stored state directly. Do not ask a model to reconstruct runtime history. Mark stale or missing observations explicitly. Show only managed or explicitly attached agents until broader discovery is verified.

The result is a compact read-only view under the [writing profile](../../guidance/writing.md). Inspection neither dispatches work nor changes acceptance. [Status](../status/SKILL.md) summarizes the same state across the session.
