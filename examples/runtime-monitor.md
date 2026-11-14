# Runtime monitor snapshot

This example uses the [monitor fields](../interface/terminal-monitor.md), [proposal fields](../plugin/skills/propose/SKILL.md), and [shared vocabulary](../controller/task-assessment.md).

All IDs, states, timestamps, quantities, settings, and evidence references are illustrative. This file creates no runtime state. Token amounts use thousands of tokens.

This snapshot represents a separate illustrative session, not a continuation of the other examples.

## Outcome and acceptance criteria

The view shows all active agents and recent outcomes at 2026-11-14 14:00 UTC. It does not change acceptance criteria.

| Task | Stable criteria summarized | Current acceptance state |
| --- | --- | --- |
| scoring | One score and downstream effect per replayed operation; distinct new requests still work | Gap awaiting audit |
| locale | Immediate page update; selected language survives navigation | Criteria met; user decision recorded |
| search | Correct results after edits; agreed latency and memory limits | Evidence incomplete |
| export | Required export fields remain correct through the supported entry point | Blocked by failed attempt |

## Assignments

| Agent | Role | Manager | Task; assignment; run | Model; effort | State and observable activity | Usage so far | Remaining central; range |
| --- | --- | --- | --- | --- | --- | --- | --- |
| M1 | Manager | User | scoring; S0; R-score | Balanced; medium | Active: repair decision recorded | 5 | 2; 1–4 |
| D1 | Developer | M1 | scoring; S3; R-score | Strong; high | Active: P2 self-check passed; report pending | 12 | 6; 4–10 |
| A1 | Auditor | M1 | scoring; S4; R-score | Balanced; medium | Waiting: repaired artifact required | 3 | 5; 3–8 |
| D2 | Developer | User | locale; L1; R-locale | Balanced; medium | Completed: C1–C2 self-checks reported | 8 | 0; 0–0 |
| I1 | Investigator | User | search; X1; R-search | Strong; high | Interrupted: measurement stopped at confirmed boundary | 6 | 4; 2–7 if resumed |
| D3 | Developer | User | export; E1; R-export | Balanced; medium | Failed: required environment unavailable | 4 | Unknown; retry not scheduled |

Model names are display capability labels for assumed resolved identifiers. In a real view, inspection shows actual confirmed settings. Usage so far is cumulative per agent in the displayed session, not only its latest assignment.

| Agent | Latest activity UTC | Blocker | Expected deliverable | Report or evidence reference |
| --- | --- | --- | --- | --- |
| M1 | 13:59 | None | Coordination decisions and acceptance assessment | Decision MD2 |
| D1 | 14:00 | None | Repaired patch and self-check report | P2 self-check evidence DC2 |
| A1 | 13:58 | Needs complete P2 handoff | P2 audit report | Prior failed audit AR1 |
| D2 | 13:40 | None | Locale patch and self-check report | L-report; checked artifact L-patch |
| I1 | 13:50 | Paused; resume reconciliation required | Measurement report and next decision | Partial evidence X-evidence |
| D3 | 13:30 | Environment unavailable | Export patch and check report | Failure event EF1; no complete assignment report |

Only passed checks and recorded milestones indicate progress. No percentage-complete value is inferred.

## Plan usage and session budget

| Provider bucket | Observation | Reset | Freshness |
| --- | --- | --- | --- |
| Coding primary | 62% used | 18:00 UTC | Observed 13:59 UTC |
| Coding secondary | Unknown | Unknown | Not supplied |

Provider percentages do not establish a token balance.

| Session accounting | Tokens |
| --- | --- |
| User session budget | 120 |
| Observed usage | 38 |
| Estimated remaining active usage: M1 and D1 | Central 8; range 5–14 |
| Active reservations: M1 and D1 upper scenarios | 14 |
| Protected waiting audit S4 | 8 |
| Protected interrupted investigation X1 resumption | 7 |
| Protected later migration audit | 20 |
| Protected future work total | 35 |
| Reserved active plus protected future work | 49 |
| Uncommitted budget | 33 |

The six usage rows total 38. Session budget 120 covers 38 observed, 14 active reservations, 35 protected, and 33 uncommitted.

The accounting window starts at 12:00 UTC. Earlier preparation lies outside its declared scope. No separate planning calls occurred within this window. All observed categories shown are confirmed through 14:00 UTC.

## Assumptions and escalation

The view uses controller state, not model-reconstructed history. Its adjustable filter includes active agents and outcomes from the previous 24 hours. Task, manager, run, and time-window filters are available.

Remaining estimates are illustrative heuristic updates at 14:00 UTC. Inspection preserves their earlier versions and assumptions.

D3's potential retry cost remains unknown and uncommitted. A retry needs a fresh estimate and policy check. I1's resumption is protected future work because interruption is confirmed; it is not an active reservation.

Provider secondary allowance is a material data gap. Delayed usage would make the token balance provisional and require an uncertainty hold. An ended failed turn is not a submitted report or task acceptance.

## Plan reference or next action

| Run | Illustrative plan reference |
| --- | --- |
| R-score | plan-scoring, revision 2 |
| R-locale | plan-locale, revision 1 |
| R-search | plan-search, revision 2 |
| R-export | plan-export, revision 1 |

Inspect D1 to see S1 and S3, their attempts, P2 evidence, and forecast history.

The next ready audit waits for D1's complete report. Normal delivery needs no new confirmation. Inspection and refresh perform no dispatch and invoke no model.
