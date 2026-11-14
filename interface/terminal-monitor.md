# Terminal monitor

The monitor presents stored controller state as a compact persistent panel or separate terminal pane. Inputs are events, reconciled state, reports, and accounting observations. Output is a read-only session and agent view.

Proposed default: use a separate pane. Native Codex footer modification remains an [integration question](../controller/codex-integration.md). Use the [writing profile](../plugin/guidance/writing.md) and [shared vocabulary](../controller/task-assessment.md).

## Budget summary

| Field | Display behavior |
| --- | --- |
| Provider allowance | Bucket label and scope, percentage with used or remaining semantics, observation time, and reset time. |
| Session budget | User token envelope and accounting scope. |
| Observed usage | Confirmed usage with freshness and any missing categories. |
| Remaining active estimate | Central value and plausible range for currently reserved assignments. |
| Reservations | Active reservation total, uncertainty margins, and protected future work separately. |
| Uncommitted budget | Amount defined by [scheduling](../controller/session-scheduling.md), marked provisional when observations are incomplete. |
| Data gaps | Missing usage, stale events, unknown allowance, and material reconciliation problems. |

Never convert quota percentages into tokens without a verified mapping. Display unknown values as unknown. Budget warnings describe planning risk, not guaranteed runtime enforcement.

## Agent fields

| Field | Meaning |
| --- | --- |
| Agent and role | Logical agent ID and assigned job profiles. |
| Manager | Reporting manager ID, or user when none exists. |
| Task and assignment | Stable task, assignment, run, and active revision references. |
| Model and effort | Current confirmed settings; distinguish intended settings when confirmation is missing. |
| State and activity | Lifecycle state and latest observable action. |
| Milestones | Completed checks, submitted reports, or confirmed artifacts. |
| Usage so far | Observed cumulative assignment or agent usage, with scope labeled. |
| Remaining usage | Central estimate and range, separate from usage so far. |
| Last activity and blocker | Timestamp and the condition preventing progress. |
| Evidence | Latest report, checked artifact, or diagnostic reference. |

Use checks and milestones for progress. Do not invent percentage-complete values from elapsed time or tokens spent.

Proposed adjustable default: show all active agents and agents completed or failed during the previous 24 hours. Waiting, reporting, interrupted, and paused unresolved agents remain visible.

Include ready and idle participants in current runs. Keep older inactive participants available through inspection and time-window filters.

Support task, manager, run, and time-window filters. Keep material excluded failures discoverable through filter summaries. Inspecting one agent reveals assignments, attempts, messages, reports, evidence, and forecast revisions.

Initial visibility covers TaskAllot-managed or explicitly attached agents. Broader host discovery and complete nested-worker accounting remain unverified.

Render routine refreshes from stored state and events without model calls. Recover missed events through controller reconciliation. Show observation age instead of presenting old state as live.

[Agents](../plugin/skills/agents/SKILL.md) and [status](../plugin/skills/status/SKILL.md) use the same fields. The [runtime example](../examples/runtime-monitor.md) demonstrates a complete snapshot.
