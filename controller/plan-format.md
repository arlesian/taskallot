# Editable plan format

This component turns preferences into a validated, versioned configuration. Inputs include user choices, proposed defaults, task briefs, estimates, and host capabilities. Output is an authoritative plan revision and a generated review view.

Use the [shared vocabulary](task-assessment.md). This document owns configuration authority; [lifecycle](agent-lifecycle.md) owns execution state.

## One configuration authority

Proposed default: JSON is the future authoritative configuration format. Markdown is its generated review view. This scaffold defines fields in prose only.

Users can request changes through [plan](../plugin/skills/plan/SKILL.md) or edit the authoritative configuration later. A validated edit creates a new revision with its parent and change origin. Regenerate the Markdown view afterward.

A Markdown annotation is an edit request, not another authoritative configuration. Reconcile it against the referenced revision before applying it. Reject stale conflicting edits and show the conflict. Do not silently merge two sources of truth.

Keep explicit user choices and inferred defaults distinguishable. Preserve previous revisions and estimates. Exact serialization, file naming, and edit interface remain [open](../OPEN-QUESTIONS.md).

## Future configuration fields

Field names below describe meaning. They do not establish a JSON schema or exact key spelling.

| Field group | Meaning and edit behavior |
| --- | --- |
| Plan ID and revision | Stable plan identity, immutable revision identity, parent reference, change summary, and choice provenance. |
| Requested outcome and acceptance criteria | User-visible result, stable criterion IDs, evidence requirements, and acceptance decision authority. |
| Tasks and priorities | Task IDs, outcomes, priority origin, and protected future work. |
| Dependencies | Prerequisites for tasks or assignments, including required reports, checked artifacts, and acceptance gates. |
| Assignments | Stable assignment IDs, task reference, accountable agent, bounded work, and completion conditions. |
| Agents and reporting | Logical agent IDs, job profiles, manager IDs or none, model identifiers, and reasoning effort. |
| Workspace and edit scope | Repository and base references, worktree policy, permitted paths, artifact locations, and allowed external effects. |
| Deliverables | Patch, report, check evidence, or decision expected from each assignment. |
| Estimates | Source, comparable history, central estimate, plausible range, assumptions, prediction time, and freshness dependencies. |
| Session budget | User token budget, accounting scope, reservation policy, protected work policy, and planning allowances. |
| Provider observations | Bucket scope, reported percentage semantics, observation time, reset time, and unavailable data. These are observations, not user-set capacity. |
| Concurrency | Maximum concurrent assignments, writer ownership, isolation requirements, and nested-delegation policy. |
| Escalation | Conditions for stronger models, revised scope, pause, user input, or budget changes. |
| Follow-up and retry boundaries | Permitted follow-up kinds, attempt or usage bounds, repair scope, and stopping conditions. |

Provider observations are snapshots attached to a revision, not editable statements of fact. Updated observations belong to runtime records and later snapshots.

## Configuration versus run records

Users choose logical agent and assignment references. The controller creates run IDs, attempt IDs, host thread mappings, message receipts, event positions, and usage observations.

Run records never become editable budget history. A model change affects future execution at supported boundaries; it does not relabel past usage.

Reservation amounts and observed usage are generated run values. Configuration defines their policy, not editable historical counters.

Starting a revision records its authorization envelope. User edits create a draft until selected for [setup](../plugin/skills/setup-agents/SKILL.md). In-scope manager follow-ups create derived revisions with recorded provenance. The controller can apply them under the existing envelope without repeated confirmation.

Derived revisions cannot widen acceptance, edit authority, allowed agent count, or spending bounds. Out-of-envelope changes wait for user input. Active assignments retain their issued revision until reconciliation records a safe transition.

Carry unchanged assignments forward explicitly. Mark replaced assignment versions superseded. A newer plan revision does not invalidate unrelated work automatically.

## Useful validation failures

| Failure | Reviewable response |
| --- | --- |
| Dependency cycle | Identify the cycle and work that cannot become ready. |
| Duplicate IDs or missing references | Name conflicting entries or unresolved targets. |
| Invalid manager reference | Identify a missing manager, missing manager profile, self-reporting, or reporting cycle. |
| Unsupported model settings | Name the unavailable model or effort; propose a substitution without overriding explicit choices. |
| Conflicting writes | Identify overlapping scopes; require isolation and an integration owner, or serialize the work. |
| Missing acceptance criteria | Block launch for the affected task; request observable criteria. |
| Unbounded follow-ups or missing authority | Identify the missing stop condition or permission. |
| Stale estimates or incompatible revision | Refresh affected predictions and show changes before reconciliation. |

For example, adding an auditor requires an agent reference, reporting relationship, checked artifact dependency, deliverable, and estimate. It does not change the task's criteria.
