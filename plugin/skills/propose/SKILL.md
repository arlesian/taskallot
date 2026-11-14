# Propose a setup

`/propose` is a working product name. This file describes future behavior, not a registered command. [Invocation evidence](../../../controller/codex-integration.md) records host conflicts and naming options.

## Purpose and boundary

Accept a task and available session context. Recommend one setup using [assessment](../../../controller/task-assessment.md), [selection](../../../controller/plan-selection.md), and [estimation](../../../controller/usage-estimation.md).

A task description alone can produce a provisional recommendation. Mark missing context unknown. State the assumptions that affect the choice.

Compare one agent with the smallest useful team when independence or separable work provides material value. Include a dedicated manager's usage when present. Show an alternative only for a material tradeoff.

The result is a recommendation. This skill starts no agents and creates no run. [Plan](../plan/SKILL.md) can persist or edit it. [Setup](../setup-agents/SKILL.md) starts a selected plan later.

## Canonical compact proposal

Use the following five fields in this order. Use the [writing profile](../../guidance/writing.md). Give one short reason when the setup needs explanation. Link detailed evidence instead of repeating it.

| Field | Required content |
| --- | --- |
| Outcome and acceptance criteria | Requested behavior and stable, observable criteria; task references when available |
| Assignments | Table with agent, role, assignment, reporting relationship, model, effort, deliverable, and usage range |
| Plan usage and session budget | Central estimate and plausible range; planning and manager costs; session budget, observed usage, active reservations, protected work, and uncommitted budget; provider allowance separately |
| Assumptions and escalation | Material unknowns, estimate source and freshness, dependencies, permitted follow-ups, and conditions requiring revision or user input |
| Plan reference or next action | Plan ID and revision if persisted; otherwise the relevant next step; indicate whether any execution has occurred |

Assignment usage is inclusive, as defined in [estimation](../../../controller/usage-estimation.md). Show a central value alongside the range. Separate observed usage from forecasts in an active run.

Actual model identifiers are required before dispatch. Capability labels can support a provisional recommendation when availability is unknown.

All [proposal examples](../../../examples/single-agent.md) use these fields. The [team example](../../../examples/multi-agent.md) includes a meaningful alternative.
