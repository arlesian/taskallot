# Inspect session status

`/status` is a working product name with a known host-command conflict. See [integration evidence](../../../controller/codex-integration.md).

This skill reads the same controller state as [agents](../agents/SKILL.md). It summarizes [budget accounting](../../../controller/session-scheduling.md), blockers, acceptance gaps, and material changes.

Show session budget, observed usage, estimated remaining active usage, reservations, protected work, and uncommitted budget. Show provider allowance buckets and reset times separately. Include observation freshness and unknown values.

Link changed assignments, reports, and decisions. Do not treat an ended turn as task acceptance. The [monitor](../../../interface/terminal-monitor.md) owns presentation fields and filters.

The output is read-only and follows the [writing profile](../../guidance/writing.md). Routine refresh reads stored state without a model call. A user-requested analysis is separate work with separately accounted usage.
