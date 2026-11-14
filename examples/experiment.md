# Experiment with uncertain remaining work

This illustrative proposal uses the [canonical fields](../plugin/skills/propose/SKILL.md) and [shared vocabulary](../controller/task-assessment.md). All values, results, references, and model capabilities are invented. No experiment ran.

Token amounts use thousands of tokens. Acceptance thresholds below belong only to this example.

## Outcome and acceptance criteria

Task `search` aims to reduce editor search latency on an agreed representative workload.

- C1: Results and ordering remain correct after edits.
- C2: The workload's measured p95 latency is at most 80 milliseconds.
- C3: Added memory use is at most 20 megabytes.

Hypothesis: a cache can meet C2 without violating C1 or C3. Compare it with the current search path under the same workload.

## Assignments

| Agent | Role | Assignment | Reports to | Model | Effort | Deliverable | Central; range |
| --- | --- | --- | --- | --- | --- | --- | --- |
| E1 | Investigator, developer | X1: run bounded comparison, choose an allowed path, implement, and self-check C1–C3 | User; no manager | Strong coding capability; identifier unresolved | High | Experiment evidence, decision, patch, checked revision, and gaps | 20; 8–34 |

The selected policy permits one measurement repeat and one bounded implementation repair within the range. A second inconclusive measurement stops for a decision.

## Plan usage and session budget

| Initial prediction component | Central tokens | Range |
| --- | --- | --- |
| Planning calls | 2 | 1–3 |
| Experiment phase within X1 | 6 | 4–8 |
| Remaining branch within X1 | 14 | 4–26 |
| Initial plan total | 22 | 9–37 |

The central planning scenario uses the rejection branch below. It is a heuristic, not a probability-weighted expectation. All phases include their context, tool output, messages, checks, and reporting.

| Possible result | Remaining work after the experiment | Remaining central; range |
| --- | --- | --- |
| Candidate succeeds | Integrate cache and check edit invalidation, latency, and memory | 6; 4–8 |
| Candidate is rejected | Replace the approach with a bounded search-index change; preserve C1–C3 | 14; 10–20 |
| Result is inconclusive | Repeat measurement once, then select supported implementation or report a blocker | Unknown; 6–26 |

The inconclusive range includes 2–6 for measurement and 4–20 for conditional implementation. Its central value remains unknown without an outcome assumption.

Before planning, assume a session budget of 70, observed usage of 10, and protected future work of 15. No other active work is reserved. Uncommitted budget is 45 before this plan and 8 after its upper reservation. Provider allowance and reset times are unknown.

## Assumptions and escalation

Source: cold-start scenarios for draft revision 1. The environment can measure comparable workloads and memory. Refresh estimates when observations select a branch.

Keep C1–C3 unchanged even if the cache fails. A new performance target, unbounded experiment loop, or broader implementation scope requires user input.

### Illustrative result and forecast revision

Assume the candidate violates C3. The permitted alternative remains in scope. Planning consumed 2 and the experiment consumed 7.

| Prediction record | Observed plan usage | Remaining central; range | Forecast plan total |
| --- | --- | --- | --- |
| Original, revision 1 | Not yet dispatched | 22; 9–37 | 22; 9–37 |
| Revised after rejection, revision 2 | 9 | 14; 10–20 | 23; 19–29 |

Keep the original prediction for evaluation. The revised total includes observed costs once; it does not add the original experiment estimate again.

Session observed usage becomes 19, including the earlier 10. Reserve 20 for remaining X1 work and retain 15 for future work. Uncommitted budget becomes 16.

## Plan reference or next action

Illustrative plan `plan-search` moves from revision 1 to derived revision 2 under the selected branch policy. No records are created here.

Before launch, use plan and setup. After the illustrative result, the controller can continue the authorized branch without another confirmation. The user assesses acceptance from E1's final evidence.
