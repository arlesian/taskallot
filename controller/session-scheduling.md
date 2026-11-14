# Session scheduling and budget policy

Scheduling selects ready work across the known session. It uses priorities, dependencies, [active forecasts](usage-estimation.md), provider observations, and the selected [plan policy](plan-format.md).

The manager proposes allocation decisions. The controller validates authority, reserves allowance, and dispatches eligible assignments. Without a manager, it advances only predefined work. See the [shared vocabulary](task-assessment.md).

## Separate budget values

| Value | Meaning |
| --- | --- |
| Provider allowance observation | Reported bucket scope, used or remaining percentage, observation time, and reset time. |
| Session token budget | User-defined token envelope with a declared accounting start and scope. |
| Observed usage | Confirmed consumption within that session scope. |
| Active reservations | Budget held for estimated remaining active assignments, including uncertain ongoing activity. |
| Protected future work | Budget held for known priority work, including dependencies not ready yet. |
| Uncommitted budget | Session budget after observed usage, active reservations, and protected future work are deducted once. |

Proposed default: reserve the upper remaining estimate for active work. State any extra uncertainty margin separately. Waiting future work belongs in protected work or an explicit uncommitted queue, not both.

Do not infer an exact token balance from a provider percentage without a verified conversion. A provider reset changes only its reported bucket. It does not replenish the user-defined session budget automatically.

Missing or delayed usage is unknown, not zero. Show a provisional budget balance and hold an explicit uncertainty reservation when appropriate. If no defensible margin exists, block additional autonomous dispatch until reconciliation.

## Allocation and reconciliation

Protect higher-priority known work before assigning uncommitted budget. Among ready tasks, consider user priority and dependency benefit. Explicit user priorities outrank inferred ones.

Update reservations when remaining estimates change. Deduct observed consumption once and replace the remaining reservation. Release unused reservations after confirmed completion. Do not release uncertain activity merely because contact was lost.

Include planning and manager calls. Reconcile already incurred planning usage against the stated snapshot. Preserve original predictions for evaluation. [Estimation](usage-estimation.md) owns token-category and aggregation rules.

Spending more now can benefit the session. A strong developer may resolve an authentication blocker that prevents several priority tasks. Repeated weak attempts can cost more and leave those tasks blocked.

Preserving allowance can be better. A routine locale fix may need one developer, leaving capacity for a later critical migration audit. A difficult critical task may deserve the stronger model while less important work waits.

## Policy actions

| Trigger | Proposed behavior |
| --- | --- |
| Overrun or new evidence | Retain spent usage, revise remaining estimates, and reconsider ready work. |
| Failure | Assess repair, investigation, or deferral; enforce bounded retry rules. |
| New priority task | Recheck dependencies and protected work before new dispatch. |
| Low allowance | Preserve critical capability; defer lower-value work or propose a scope revision. |
| Pause | Stop new dispatch and request a safe execution boundary. Record effects that may already have occurred. |
| Resume | Reconcile activity, allowance, evidence, and estimates before continuing. |
| Confirmed reset | Refresh the affected provider bucket; reconsider deferred work without inventing a token conversion. |
| Scope or authority expansion | Request user input under the [setup boundary](../plugin/skills/setup-agents/SKILL.md). |

Normal authorized handoffs and bounded repairs proceed without repeated confirmation. A manager can choose among permitted follow-ups but cannot expand the authorization envelope.

Planning thresholds are not hard runtime token limits. Usage events may arrive late, and an in-flight turn can overshoot a reservation or budget. Check before dispatch and at observable boundaries. Request interruption when policy requires it, then reconcile actual effects.

Do not claim immediate cancellation, exact cutoff, or rollback without verified host support. Reservation margins, stale-data thresholds, reset handling, and priority tie-breaking remain [open](../OPEN-QUESTIONS.md).
