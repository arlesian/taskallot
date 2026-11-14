# Task assessment and shared vocabulary

Assessment turns user intent and available session context into a task brief. The brief supports [selection](plan-selection.md), [estimation](usage-estimation.md), and [plan editing](plan-format.md).

## Shared vocabulary

These definitions govern the scaffold.

| Term | Meaning |
| --- | --- |
| Role | A reusable job profile with responsibility, authority, deliverables, and completion conditions. |
| Agent | A runtime participant with an identity, model, reasoning setting, and assigned roles. |
| Task | A user-relevant outcome with acceptance criteria. |
| Assignment | A bounded piece of task work given to one accountable agent. |
| Plan | The versioned description of tasks, assignments, agents, dependencies, and budget policy. |
| Run | One execution instance of a plan, including later revisions and actual results. |
| Manager | The agent responsible for coordination and work allocation. |
| Controller | The software that maintains state, delivers messages, dispatches work, and accounts for usage. |

Several agents can contribute assignments to one task. A role does not imply a separate agent. An assignment names its owner, boundaries, deliverable, and relevant acceptance criteria.

The initial job profiles are [manager](../plugin/roles/manager.md), [investigator](../plugin/roles/investigator.md), [developer](../plugin/roles/developer.md), [auditor](../plugin/roles/auditor.md), and [reviewer](../plugin/roles/reviewer.md). Future profiles can extend this vocabulary.

## Inputs and output

Use the requested outcome, known behavior, repository context, uncertainty, difficulty, and failure consequences. Include session priorities, dependencies, available models, and allowance observations when available.

The output identifies acceptance criteria, likely scope, evidence gaps, and useful assignment boundaries. Separate supplied facts from assumptions. A task description alone supports a provisional brief.

Do not treat future discoveries as available evidence. Preserve acceptance criteria through delegation. A manager can divide work without weakening the task outcome. Criterion changes require a recorded plan revision and appropriate user authorization.

For example, the locale task requires an immediate language change on the current page. A developer can diagnose, implement, and self-check that behavior. This does not establish independent review.

## Distinct outcomes and their records

The controller owns each authoritative record. The evidence producer and decision authority differ.

| Outcome | Evidence or decision source | Controller record |
| --- | --- | --- |
| An agent turn ended | Host event with completed, failed, or interrupted status | Turn result and host references; no inferred assignment completion |
| An assignment report was submitted | Agent submits a complete report | Durable report reference, assignment status, and receipt |
| Required checks passed | Developer or auditor supplies results for a specific artifact revision | Check outcomes, checked revision, evidence, and unavailable checks |
| The task met its acceptance criteria | Manager assesses evidence under the plan's acceptance policy; user decides when no manager exists | Criterion-level decision, authority, evidence references, and unresolved gaps |

A report can contain failures. Passing checks can still leave acceptance gaps. The controller records a manager's assessment; it does not invent one from agent inactivity. User acceptance remains a separate evaluation outcome.
