# Agent lifecycle and recovery

The controller maps selected [plan revisions](plan-format.md) to host activity. It uses dependency state, authorization, reservations, messages, and host observations. Its output is reconciled run state and permitted dispatch.

Use the [shared vocabulary](task-assessment.md). Agent activity, assignment completion, and task acceptance are separate records.

## States and transitions

| State or event | Required behavior |
| --- | --- |
| Created | Record logical agent, roles, model, effort, workspace, run, and host mapping when available. |
| Ready | Confirm dependencies, scope, model support, budget reservation, and authorization before dispatch. |
| Active | Record the assignment and attempt. Observe host events, milestones, and usage without inventing progress. |
| Waiting | Name the dependency, report, answer, permission, or budget condition. Idle time is not failure. |
| Reporting | Accept a complete report and publish its durable reference. Wait for a disposition where required. |
| Idle | Assignment has a disposition and no turn is active. Reuse remains possible. |
| Failed | Record failure evidence, partial artifacts, usage, and unresolved effects. Reconcile before retry. |
| Interrupted or paused | Record the last confirmed execution boundary and incomplete effects. Do not infer rollback. |
| Completed | Record the agent's finished scope. Task acceptance still requires its own evidence and decision. |
| Resuming | Inspect previous attempts, reports, artifacts, and host activity before continuing or replacing work. |

Proposed initial default: one active assignment per worker, including the manager. A coordination assignment can span several short manager turns. Waiting assignments hold no active host turn unless explicitly reported otherwise.

## Reuse and independence

Reuse an idle agent when its context remains useful and compatible with the assignment. Use a fresh agent when context is misleading, permissions differ, or independence requires a separate reasoning context.

Model or effort changes apply at supported execution boundaries, usually before a new turn. Record the change and refresh remaining estimates. If unsupported, use a new agent with a bounded handoff. Do not interrupt solely to pretend a setting changed mid-turn.

## Recovery and duplicate prevention

[Communication](agent-communication.md) owns stable IDs and delivery recovery. Before dispatch, persist the attempt's intent. After dispatch, retain host thread and turn references.

On controller restart, reconcile recorded intents with host activity and durable reports. Rebuild views from records without asking agents to recreate history. A lost connection means unknown activity, not zero usage or completed work.

Resume first checks whether the assignment already ran. Reuse an active attempt, consume an existing report, or continue from confirmed partial work. Start a new attempt only after duplicate-sensitive effects are resolved.

After partial startup failure, retain successfully created agents and active attempts. Retry only the missing or failed startup operations. An uncertain launch remains blocked until reconciled.

Record stale observations with their last confirmed time. An expired freshness threshold triggers inspection and a visible warning, not automatic replacement execution. Thresholds remain [open](../OPEN-QUESTIONS.md).

After failure or interruption, retain observed usage and revise estimated remaining work. Preserve reservations for uncertain ongoing activity. Release them only after activity ends or a justified reconciliation replaces them.

## Manager and controller boundaries

The manager makes engineering allocation and acceptance assessments within plan authority. The controller validates policy, maintains state, delivers records, and dispatches allowed work.

Without a manager, the controller handles dependencies, predefined assignments, receipts, reservations, status, and bounded retry rules. The developer reports to the user. New judgment-dependent work waits for user input or a selected revised plan.

## Nested workers and runtime controls

Initial visibility covers TaskAllot-managed or explicitly attached agents. Any harness-created child must receive a run mapping, ownership, allowance reservation, and usage attribution before execution.

Proposed initial policy prohibits unaccounted nested delegation. Managers request workers through the controller. They do not spawn hidden workers directly.

Use verified host controls to disable unmanaged delegation where available. If the host cannot enforce or expose this boundary, report that limitation and decline autonomous nested execution.

Role descriptions and `AGENTS.md` provide guidance. They do not automatically enforce filesystem authority, tool restrictions, concurrency, or spending limits. [Integration](codex-integration.md) records documented capabilities and prototype gaps.
