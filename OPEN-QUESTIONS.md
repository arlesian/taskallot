# Decisions to review

These defaults are proposals, not implemented behavior. Change each decision in its linked home. Then update affected examples and views.

| Choice | Proposed default | Owning description |
| --- | --- | --- |
| Invocation names and host conflicts | Keep product labels; consider `taskallot-` prefixed skills and verified explicit invocation. Do not claim custom slash commands. | [Integration](controller/codex-integration.md) |
| Plugin packaging and controller startup | Package user guidance as a plugin and use a small local controller. Verify discovery and startup before choosing distribution. | [Manifest outline](plugin/manifest-outline.md) |
| Controller language and storage engine | Choose the smallest local implementation that supports durable writes and recovery. No engine or language is selected. | [Lifecycle](controller/agent-lifecycle.md), [communication](controller/agent-communication.md) |
| Plan editing | Use authoritative JSON revisions and generated Markdown views. Treat Markdown annotations as change requests against a revision. Exact editing UI and serialization remain open. | [Plan format](controller/plan-format.md) |
| Running revision changes | Apply in-scope manager-derived revisions under existing authority. Keep user-edited drafts inactive until selected for reconciliation. | [Plan format](controller/plan-format.md) |
| Role authority | Scope diagnostic and test artifacts to the assignment. Managers coordinate; developers implement source changes. Runtime enforcement needs a host mapping. | [Job profiles](plugin/roles/manager.md), [integration](controller/codex-integration.md) |
| Acceptance authority without a manager | Developer supplies self-check evidence; user decides task acceptance. Controller records the distinction. | [Task assessment](controller/task-assessment.md) |
| Manager use | Omit a dedicated manager for small cohesive runs. Include one when dependencies and follow-ups need coordination; count its usage. | [Selection](controller/plan-selection.md) |
| Communication policy | Use targeted durable messages and report references. Permit worker questions; notify managers of scope, ownership, and interface decisions. | [Communication](controller/agent-communication.md) |
| Delivery and incomplete writes | Reconcile repeated delivery, publish complete reports only, and block uncertain relaunches. Exact durable-write and recovery mechanics need a prototype. | [Communication](controller/agent-communication.md) |
| Concurrency | Start with one active assignment per agent and separate worktrees for concurrent writers. Set overall concurrency per plan; serialize conflicting integration. | [Lifecycle](controller/agent-lifecycle.md), [concurrency guide](plugin/guidance/concurrency.md) |
| Nested delegation | Prevent unaccounted children. Use controller dispatch and verified host controls; decline unsupported autonomous nesting. | [Lifecycle](controller/agent-lifecycle.md) |
| Model and effort routing | Resolve actual supported identifiers before dispatch. Use difficulty, uncertainty, expected acceptance, repair exposure, and remaining allowance. No fixed model list or routing threshold yet. | [Selection](controller/plan-selection.md) |
| Estimate calibration | Begin with comparable historical central values and conservative ranges. Use heuristic branches when history is weak. Exact statistics and coverage targets remain open. | [Estimation](controller/usage-estimation.md) |
| Later trained predictor | Compare a separately trained predictor against the baseline. Do not choose architecture, training-data requirements, or adoption thresholds yet. | [Estimation](controller/usage-estimation.md) |
| Reservations and accounting gaps | Reserve upper remaining scenarios and protect future priority work. Show unknown usage and explicit uncertainty holds. Margins remain open. | [Scheduling](controller/session-scheduling.md) |
| Budget enforcement | Check before dispatch and at observed boundaries. Explain delay and possible overshoot. Do not promise hard cutoffs without host support. | [Scheduling](controller/session-scheduling.md) |
| Follow-ups and retries | Select bounded kinds, attempts, repair exposure, and stop conditions per plan. Normal in-scope work needs no repeated confirmation. No universal retry count is fixed. | [Setup](plugin/skills/setup-agents/SKILL.md), [plan format](controller/plan-format.md) |
| Freshness and resets | Refresh before launch or resume and after material changes. Preserve bucket scope and reset timestamps. Exact age thresholds remain open. | [Scheduling](controller/session-scheduling.md) |
| Terminal integration and visibility | Use a separate pane showing managed or attached agents. Default to active plus recent 24-hour outcomes; keep the window adjustable. Native footer and broader discovery need verification. | [Monitor](interface/terminal-monitor.md) |
| Record retention and privacy | Preserve original estimates, revisions, reports, and outcome evidence. Decide retention, redaction, attachment access, and cleanup before implementation. | [Communication](controller/agent-communication.md), [evaluation](evaluation/outcomes.md) |
| Evaluation policy | Compare priority work and repair-adjusted costs under equal allowances. Include fixed-model baselines and cold-start results. Baseline settings and decision thresholds remain open. | [Evaluation](evaluation/outcomes.md) |
| Writing profile | Apply selective STE principles and exact technical fidelity. Use manual review; claim no score or certification. | [Writing](plugin/guidance/writing.md) |
| Future vocabulary changes | Extend reusable job profiles only when responsibility, authority, deliverables, and completion conditions justify a distinct profile. | [Shared vocabulary](controller/task-assessment.md) |
