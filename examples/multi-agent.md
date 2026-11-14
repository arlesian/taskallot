# Multiple-agent proposal: duplicate essay scoring

This example follows the [canonical format](../plugin/skills/propose/SKILL.md). All token amounts, allowance snapshots, and model capabilities below are illustrative assumptions, not measurements or verified availability.

## Task and context

An interrupted callback may cause an essay to be scored twice. Acceptance requires that replaying the same scoring operation after interruption produces one recorded score and no duplicate downstream scoring effects. A genuinely new scoring request must remain distinguishable from a replay. Confirm the operation identity and effect boundaries during investigation.

This is provisionally a difficult correctness problem involving retries and durable effects. Assume strong and balanced coding models with high and medium effort are available. A later migration audit has a high estimate of 20,000 tokens, is higher priority, and depends on an external artifact that has not arrived. Other active work is already reserved.

## Recommended workers

| Worker | Assignment and role primitives | Model and effort | Deliverable and completion | Typical tokens | High tokens |
| --- | --- | --- | --- | --- | --- |
| Fix worker | Trace callback interruption and replay, implement the fix, and check the affected flow; investigate, implement, verify | Strong coding model, high effort; actual identifier unverified | Causal evidence, patch, check results, and integration of findings; complete when checks and agreed bounded repairs are reported, or blocked | 14,000 | 24,000 |
| Independent worker | Derive interruption cases from requirements, verify them against the fix, and review the change; investigate, verify, review | Balanced coding model, medium effort; actual identifier unverified | Independently derived cases, results, and prioritized findings; complete when conditions have evidence or explicit gaps and blockers | 6,000 | 10,000 |

Both receive the same acceptance conditions and relevant interface facts. Initially withhold the fix worker's diagnosis and patch from the independent worker so it can derive cases separately. Case derivation can run in parallel with diagnosis and implementation. Then hand over the patch and notes for verification and review. The fix worker owns integration of findings and the bounded repair already allowed for in its estimate; the independent worker rechecks affected cases within its allowance.

## Why this plan

Compare one strong agent with this two-agent team. One agent could diagnose, fix, and test the flow, but its tests may repeat the assumption behind the patch. Independent case derivation can expose interruption after recording a score but before callback acknowledgement, or confusion between a replay and a new request. The second worker adds a different view of the failure boundary, not another implementation owner. Two workers are the smallest useful team for that benefit.

A meaningful alternative under tighter allowance is one strong coding worker at high effort, assigned investigate, implement, verify, and review, with review explicitly performed as self-review. It delivers the patch, failure-case analysis, and check evidence, completing with evidenced conditions or reported gaps. Its illustrative worker estimate is 16,000 typical and 27,000 high tokens, reflecting added case derivation and self-review despite fewer handoffs. The same controller overhead of 3,000 and 5,000 gives a 19,000 typical and 32,000 high plan. This saves 4,000 typical or 7,000 high tokens relative to the team, but loses independent challenge.

## Usage and uncertainty

| Component | Typical tokens | High tokens |
| --- | --- | --- |
| Controller planning and proposal, including alternative comparison | 3,000 | 5,000 |
| Fix worker, inclusive | 14,000 | 24,000 |
| Independent worker, inclusive | 6,000 | 10,000 |
| Estimated plan total | 23,000 | 39,000 |

These are cold-start heuristic scenarios based on the symptom, expected effect boundaries, and bounded assignments. Worker totals include initial and repeated context, producing and consuming handoff notes, checks, and reports. Typical assumes a focused repair with routine iteration; high includes one repair cycle responding to independent findings and a recheck. A storage redesign or repeated unsuccessful repairs is outside the estimate. Uncertainty is high because callback identity, persistence behavior, and downstream effects are unconfirmed. Summed high estimates are a conservative scenario, not a confidence guarantee.

## Session implications

At planning start, assume a user-supplied remaining token envelope of 70,000 and high remaining reservations of 8,000 for other active work. There are 62,000 tokens available before this plan. Provider quota percentage and reset time are unknown.

The team leaves 39,000 tokens under typical usage or 23,000 under high usage after active reservations. Protecting the later migration audit's 20,000 high estimate leaves 19,000 or 3,000 for other unstarted work. Planning usage is included from the snapshot and must be reconciled once. If the audit artifact arrives, its priority changes the next dispatch decision.

If only 34,000 tokens were available for this task after active reservations and protected later work, the team's 39,000 high scenario would not fit. The one-agent alternative's 32,000 high scenario would leave 2,000. Recommend that alternative only with the independence tradeoff visible. If even that cannot fit, propose deferral or a bounded investigation with a new estimate; do not call a partial investigation a completed fix. An unconfirmed quota reset is not a reason to spend the protected allowance.

## Assumptions and escalation

Assume operation identity can be established and the relevant scoring effects can be observed. Escalate if independent cases reveal a durable-effect boundary the patch cannot protect, or if the balanced model cannot assess the failure cases adequately. Additional model strength or a redesigned persistence approach needs new estimates and a revised proposal. On overrun or failure, retain usage already spent, replace remaining reservations, and reassess whether repair or deferral best protects session priorities.

## Decision and edits

Recommend the two-worker team under the main illustrative snapshot because independent failure analysis adds value and preserves the later audit allowance. Availability, priorities, and acceptance boundaries still need confirmation. No workers have started. The user can edit the team, case scope, model choices, or budget assumptions; refresh estimates and session implications before a separate execution decision.
