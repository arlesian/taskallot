# Managed team: duplicate essay scoring

This illustrative proposal uses the [canonical fields](../plugin/skills/propose/SKILL.md) and [shared vocabulary](../controller/task-assessment.md). All IDs, quantities, artifacts, results, and model capabilities are invented. No agents or checks ran.

Token amounts use thousands of tokens. Ranges are heuristic scenarios.

## Outcome and acceptance criteria

An interrupted callback can cause duplicate essay scoring. Task `scoring` requires:

- C1: Replay of the same scoring operation produces one recorded score and no duplicate downstream scoring effects.
- C2: A genuinely new scoring request remains distinct and can complete normally.

Use a manager, developer, and independent auditor. Independent interruption cases can expose assumptions shared by a patch and its developer's self-checks.

## Assignments

| Agent | Role | Assignment | Reports to | Model | Effort | Deliverable | Central; range |
| --- | --- | --- | --- | --- | --- | --- | --- |
| M1 | Manager | S0: coordinate, allocate bounded follow-ups, and assess C1–C2 | User | Balanced coding capability | Medium | Decisions, gap tracking, acceptance assessment | 3; 2–6 |
| D1 | Developer | S1: trace and fix replay; integrate one bounded repair if needed | M1 | Strong coding capability | High | Patch, causal evidence, self-checks, and handoff | 16; 10–26 |
| A1 | Auditor | S2: derive independent cases, audit the patch, and recheck one repair | M1 | Balanced coding capability | Medium | Checked revision, failure cases, results, and gaps | 8; 5–13 |

Actual model identifiers remain unresolved. M1 owns coordination, not source implementation. D1 owns integration in its assigned workspace.

A1 first derives cases without D1's diagnosis. That work can overlap S1. Patch execution waits for D1's artifact reference. Any repaired patch requires affected checks to run again.

## Plan usage and session budget

| Component | Central tokens | Range |
| --- | --- | --- |
| Planning model calls, including comparison | 3 | 1–5 |
| Manager M1 | 3 | 2–6 |
| Developer D1, including bounded repair | 16 | 10–26 |
| Auditor A1, including recheck | 8 | 5–13 |
| Team total | 30 | 18–50 |

Inclusive estimates cover context, tools, messages, reports, and checks. The repair exposure is not an additional charge above these rows.

| Session snapshot before planning | Tokens |
| --- | --- |
| User session budget | 100 |
| Previously observed usage | 20 |
| Other active reservations | 8 |
| Protected future migration audit | 20 |
| Uncommitted before this plan | 52 |
| Uncommitted after reserving the team's upper scenario | 2 |

Central consumption would leave 22 uncommitted with other holds unchanged. Provider allowance and reset times are unknown.

### Material alternative under tighter allowance

| Agent | Role | Assignment | Reports to | Model | Effort | Deliverable | Central; range |
| --- | --- | --- | --- | --- | --- | --- | --- |
| D2 | Developer | Diagnose, fix, derive failure cases, and self-check C1–C2 | User; no manager | Strong coding capability; identifier unresolved | High | Patch, failure-case evidence, checked revision, and gaps | 24; 16–37 |

With the same planning estimate, this plan totals 27, range 17–42. Compared with the team, it saves 3,000 central or 8,000 upper-scenario tokens.

If only 44 were available after other holds, the team would not fit its upper scenario. This alternative would leave 2. It preserves behavioral checks but loses independent assessment. If that assurance is required, defer instead.

## Assumptions and escalation

Source: cold-start heuristics for this draft. Operation identity, persistence, and downstream effect boundaries remain unconfirmed. Refresh estimates after findings or model resolution.

The team policy permits one repair assignment and one affected-case recheck within its selected scope and budget. Repeated failure, storage redesign, or broader authority requires a revised decision.

Preserve C1–C2 through every handoff. Stop for user input only when the authorization envelope must expand. Normal reports and bounded follow-ups need no repeated confirmation.

## Plan reference or next action

Illustrative draft: `plan-scoring`, revision 1. Persist and select it before setup. The following cycle describes future behavior only.

| Step | Illustrative record or action |
| --- | --- |
| Start | Setup creates run `R-score`, records S0–S2, and dispatches ready work. |
| Report | A1 submits report `AR1` for patch `P1`: interruption after recording a score repeats a downstream effect. C1 fails; C2 passes. |
| Decision | M1 records the blocking gap and issues follow-up S3 to D1. S3 covers only the exposed boundary and fits the existing repair allowance. |
| Delivery | Controller records derived revision 2 and delivers S3 once as an assignment. Repeated notification does not create another attempt automatically. |
| Repair | D1 submits patch `P2` and report `DR2`. M1 assigns the permitted recheck S4 to A1. |
| Evidence | Report `AR2` identifies P2 and checks interruption before and after each effect, concurrent replay, and a distinct new request. C1–C2 pass in the stated environment. |
| Acceptance | M1 records its assessment with AR2 and remaining limits. Controller records criterion decisions. User acceptance is recorded separately. |

The repair allowance is assigned to S3 and S4 when needed, not reserved again. Missing receipts or uncertain launch state trigger reconciliation before any retry.
