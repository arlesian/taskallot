# Durable agent communication

This component delivers bounded assignments, questions, reports, and decisions. It uses the [plan](plan-format.md), [lifecycle](agent-lifecycle.md), and [shared vocabulary](task-assessment.md).

Its output is a durable communication record and targeted delivery. The controller owns authoritative task state and accounting. Agents must not overwrite shared counters independently.

## Proposed runtime locations

These paths describe future records. They are not created by this scaffold.

| Proposed path | Purpose |
| --- | --- |
| `.taskallot/plans/` | Authoritative plan revisions and generated review views. |
| `.taskallot/runs/<run-id>/agents/<agent-id>/inbox/` | Durable targeted assignments, questions, decisions, and report notices. |
| `.taskallot/runs/<run-id>/agents/<agent-id>/reports/` | Complete reports and evidence references. |
| `.taskallot/runs/<run-id>/events.jsonl` | Ordered lifecycle, delivery, decision, and accounting observations. |

These directories preserve communication records. The controller reconciles them into authoritative state. Storage engine and write mechanics remain open.

Keep mailboxes separate from source-code workspaces. Concurrent source writers use separate worktrees by proposed default. [Concurrency guidance](../plugin/guidance/concurrency.md) owns code ownership and integration practices.

## Normal team cycle

1. The manager assigns bounded work under the selected plan.
2. The controller records the assignment and delivers it to the accountable agent.
3. The agent performs the work and submits a report.
4. The controller delivers the report reference to the manager.
5. The manager assesses acceptance evidence, repair, investigation, or dependent work.
6. The controller dispatches the resulting assignment when policy and dependencies permit it.

Normal in-scope handoffs need no new user confirmation. [Setup](../plugin/skills/setup-agents/SKILL.md) owns that authorization boundary.

Targeted worker-to-worker questions are allowed when they reduce uncertainty. Route them through the controller. Record decisions that affect scope, ownership, or interfaces, and notify the manager.

Avoid routine broadcasts. Event notifications carry references and compact state summaries. Detailed evidence stays in reports under the [writing profile](../plugin/guidance/writing.md).

## Message and report fields

| Field | Meaning |
| --- | --- |
| Message ID | Stable identity reused for redelivery of the same message. |
| References | Sender, recipient, task, plan revision, run, assignment, and attempt when relevant. |
| Type | Assignment, question, answer, report notice, decision, acknowledgement, or control request. |
| Summary and artifacts | Concise decision-relevant text plus report, patch, checked revision, and evidence references. |
| Delivery state | Recorded, delivered, acknowledged, superseded, or failed, with timestamps and failure reasons. |
| Acknowledgement | Receipt or processing acknowledgement; neither implies successful work or task acceptance. |

A report identifies its assignment and checked artifact. It separates changes, observations, passed checks, failed checks, unavailable checks, blockers, usage gaps, and recommended next actions.

## Interruption and repeated delivery

Preserve stable assignment IDs across notification retries. Execution attempts have distinct IDs. Repeated delivery must not create another assignment or host turn automatically.

The controller records dispatch intent and known host mappings before treating work as launched. After uncertain delivery, reconcile host state and artifact evidence. If execution cannot be determined, mark it uncertain and block automatic relaunch.

IDs support duplicate detection; they do not guarantee exactly-once execution. External effects can occur before a receipt survives. Assignments must identify replay-sensitive effects and their recovery checks.

Publish a report only after its contents and references are complete. Keep incomplete writes invisible to consumers and retain them for recovery. Never treat a truncated report as an acceptance decision.

Preserve submitted reports and evidence. Correct them through a linked amendment or superseding report. Validate assignments against the effective run revision before dispatch. Reject superseded assignment versions. Mark superseded reports historical rather than deleting them.

On duplicate notices, recipients acknowledge the existing assignment and report its state without repeating work. On superseded notices, recipients hold new effects and request disposition. Preserve partial artifacts and actual costs; supersession does not undo effects.

Notifications are an optimization. On reconnect or missed notification, scan durable unacknowledged records from the last known position. Deduplicate receipts and decisions before applying their effects.
