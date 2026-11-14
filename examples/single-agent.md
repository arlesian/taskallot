# Single developer: language selector

This illustrative proposal uses the [canonical fields](../plugin/skills/propose/SKILL.md) and [shared vocabulary](../controller/task-assessment.md). All IDs, quantities, and model capabilities are invented. No work ran.

Token amounts use thousands of tokens. A range shows lower and upper scenarios, not calibrated coverage.

## Outcome and acceptance criteria

The language selector updates the visible page only after navigation. Task `locale` requires:

- C1: Selecting a language updates the current page without navigation.
- C2: Later navigation preserves the selected language and existing selection behavior.

One developer can trace the state flow, implement the change, and self-check both criteria. Shared context outweighs any currently identified reason to split.

## Assignments

| Agent | Role | Assignment | Reports to | Model | Effort | Deliverable | Central; range |
| --- | --- | --- | --- | --- | --- | --- | --- |
| D1 | Developer | L1: diagnose, fix, and self-check C1–C2 | User; no manager | Balanced coding capability; identifier unresolved | Medium | Patch, cause, checked revision, results, and gaps | 8; 5–16 |

This is self-checking, not independent audit or review. A dedicated manager offers little benefit for this bounded task.

## Plan usage and session budget

| Component | Central tokens | Range |
| --- | --- | --- |
| Planning model calls | 2 | 1–4 |
| D1, including context, checks, reports, and one bounded repair | 8 | 5–16 |
| Plan total | 10 | 6–20 |

| Session snapshot before planning | Tokens |
| --- | --- |
| User session budget | 50 |
| Previously observed usage | 10 |
| Other active reservations | 6 |
| Protected future migration check | 12 |
| Uncommitted before this plan | 22 |
| Uncommitted after reserving this plan's upper scenario | 2 |

If this plan consumes its central estimate, 12 remains uncommitted with other holds unchanged. Provider allowance and reset times are unknown. These token amounts do not imply provider capacity.

## Assumptions and escalation

Source: cold-start heuristic created for this illustrative draft. No repository evidence establishes a local state defect yet. Refresh after scope or model changes.

The range includes supplied context, tool output, reporting, routine iteration, and one repair with recheck. No handoff or manager cost is included.

Cross-process caching, inaccessible page behavior, or a translation service defect requires re-estimation. Preserve C1–C2. Report unavailable checks as gaps.

The selected policy can allow one in-scope repair. Broader source authority, extra agents, or spending beyond its envelope needs user input.

## Plan reference or next action

Illustrative draft reference: `plan-locale`, revision 1. This example creates no persisted plan or runtime records.

Use [plan](../plugin/skills/plan/SKILL.md) to edit or persist the recommendation. A later [setup](../plugin/skills/setup-agents/SKILL.md) starts the selected revision. Without a manager, the controller handles predefined work and accounting; the user assesses task acceptance.
