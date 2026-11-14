# TaskAllot design scaffold

TaskAllot helps users plan, assign, and monitor software-development agents within a session budget.

The proposed product combines user-facing plugin skills with a small local controller. It supports conditional estimates, model selection, editable plans, bounded autonomous work, durable reports, and current agent status.

This repository contains design prose only. No plugin, controller, runtime state, or trained predictor is implemented here. Proposed defaults remain reviewable.

Start with the [team example](examples/multi-agent.md) and [open decisions](OPEN-QUESTIONS.md). The [shared vocabulary](controller/task-assessment.md) defines terms once.

## Design map

| Area | Authoritative homes |
| --- | --- |
| User-facing skills | [Propose](plugin/skills/propose/SKILL.md), [plan](plugin/skills/plan/SKILL.md), [setup agents](plugin/skills/setup-agents/SKILL.md), [agents](plugin/skills/agents/SKILL.md), [status](plugin/skills/status/SKILL.md) |
| Job profiles | [Manager](plugin/roles/manager.md), [investigator](plugin/roles/investigator.md), [developer](plugin/roles/developer.md), [auditor](plugin/roles/auditor.md), [reviewer](plugin/roles/reviewer.md) |
| Shared guidance | [Writing](plugin/guidance/writing.md), [engineering](plugin/guidance/engineering.md), [debugging](plugin/guidance/debugging.md), [experiments](plugin/guidance/experiments.md), [concurrency](plugin/guidance/concurrency.md), [review](plugin/guidance/review.md) |
| Controller decisions | [Assessment and vocabulary](controller/task-assessment.md), [plan format](controller/plan-format.md), [estimation](controller/usage-estimation.md), [selection](controller/plan-selection.md), [scheduling and budget](controller/session-scheduling.md) |
| Future runtime mechanisms | [Lifecycle](controller/agent-lifecycle.md), [communication](controller/agent-communication.md), [Codex integration evidence](controller/codex-integration.md) |
| Terminal presentation | [Monitor](interface/terminal-monitor.md) |
| Evaluation | [Outcomes and policy comparisons](evaluation/outcomes.md) |
| Research and packaging | [Design sources](docs/design-sources.md), [manifest outline](plugin/manifest-outline.md) |

The five slash-style names are working product names. Actual invocation and host-command conflicts are documented in [integration](controller/codex-integration.md).

Propose recommends. Plan prepares persisted configuration. Setup starts or resumes selected work. Agents and status read the same controller state.

## Review examples

- [Single developer](examples/single-agent.md): immediate locale updates with self-checking.
- [Managed team](examples/multi-agent.md): duplicate scoring, independent audit, and bounded repair.
- [Experiment](examples/experiment.md): uncertain results and revised remaining estimates.
- [Runtime monitor](examples/runtime-monitor.md): active and recent work with separate allowance and budget values.

All example values and outcomes are illustrative. [Contributor instructions](AGENTS.md) govern changes to this repository.
