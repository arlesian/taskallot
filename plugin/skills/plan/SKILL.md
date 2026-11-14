# Create or edit a plan

`/plan` is a working product name with a known host-command conflict. See [invocation evidence](../../../controller/codex-integration.md).

This skill turns user preferences or a proposal into a persisted [plan](../../../controller/plan-format.md). It uses the [shared vocabulary](../../../controller/task-assessment.md) and [writing profile](../../guidance/writing.md).

Accept agent count, roles, models, effort, reporting relationships, tasks, dependencies, workspace scope, and budget policy. Accept partial preferences. Propose missing values and label their origin.

Record explicit user choices separately from inferred defaults. Preserve acceptance criteria unless the user changes them. Explain any conflict between requested settings and available capabilities.

Refresh estimates affected by an edit. Validate the result using the [plan rules](../../../controller/plan-format.md). Save a new authoritative revision for material changes. Generate a Markdown review view from that revision.

The output includes the compact [proposal fields](../propose/SKILL.md), revision reference, material changes, and validation gaps. For example, removing an auditor changes independence, assignments, estimates, and acceptance evidence requirements.

This skill prepares configuration without starting work. Editing a running plan creates a draft revision; it does not silently replace active assignments. [Setup](../setup-agents/SKILL.md) reconciles a selected revision with its run.
