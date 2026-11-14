# Taskallot: design scaffold

Taskallot is a proposed Codex plugin for choosing agent setups for software development within a session budget. Its working interaction name is `/propose`. This repository contains editable design prose, not an installable plugin. Invocation syntax, packaging, and integration remain open.

Start with the [proposal skill](plugin/skills/propose/SKILL.md), the [single-agent example](examples/single-agent.md), and the [open decisions](OPEN-QUESTIONS.md). The [multiple-agent example](examples/multi-agent.md) shows when independent work can justify extra usage.

## Design map

| Decision | Home |
| --- | --- |
| Interaction boundary and canonical proposal format | [Propose skill](plugin/skills/propose/SKILL.md) |
| Plugin responsibilities and possible packaging contents | [Manifest outline](plugin/manifest-outline.md) |
| Vocabulary, task inputs, and acceptance conditions | [Task assessment](controller/task-assessment.md) |
| Role responsibilities and completion | [Investigate](plugin/roles/investigate.md), [implement](plugin/roles/implement.md), [verify](plugin/roles/verify.md), [review](plugin/roles/review.md) |
| Pre-dispatch token prediction | [Usage estimation](controller/usage-estimation.md) |
| Team, model, and effort selection | [Plan selection](controller/plan-selection.md) |
| Session allocation and revisions | [Session scheduling](controller/session-scheduling.md) |
| Desired Codex capabilities and unverified integration | [Codex integration](controller/codex-integration.md) |
| Prediction accuracy and useful work completed | [Evaluation](evaluation/outcomes.md) |

All example quantities are illustrative, not measurements or provider promises. Proposed defaults are reviewable choices, collected in [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md). Contributor instructions live in [AGENTS.md](AGENTS.md).
