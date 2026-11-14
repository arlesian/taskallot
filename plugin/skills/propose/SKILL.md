# Propose an agent setup

This is a prose skill design, not a packaged or registered skill. `/propose` is the working name for asking which workers, models, and reasoning efforts suit a coding task within the session's allowance.

## Interaction contract

Accept a task description and use other session work, priorities, dependencies, available models, and remaining allowance when supplied or accessible. A task description alone is sufficient for a provisional recommendation: mark missing information unknown and state assumptions. Do not require worker investigation to produce the first proposal.

Calling `/propose` produces a proposal only. It starts no workers and authorizes no implementation. The user can edit assignments, acceptance conditions, model choices, effort, and budget assumptions. Refresh affected estimates and session implications after edits. A later, separate execution decision is outside this interaction; its Codex mechanism is [unverified](../../../controller/codex-integration.md).

Use [task assessment](../../../controller/task-assessment.md) for terms and acceptance conditions, [role descriptions](../../roles/investigate.md) for assignments, [usage estimation](../../../controller/usage-estimation.md) for predictions, [plan selection](../../../controller/plan-selection.md) for the recommendation, and [session scheduling](../../../controller/session-scheduling.md) for effects on other work.

## Canonical proposal format

Use these seven sections in order. Include unknown fields explicitly. Tables may grow to fit the recommendation; do not invent missing facts to fill them.

COMMENT: this plugin prioritizes agentic programming efficiency. so make the proposal concise; include only necessary analytics(mostly should be quantitative). readability is key. follow ASD-STE100 format about 80%.

### Task and context

State the requested outcome, acceptance conditions, task difficulty and coupling, known session work and dependencies, and available model information. Identify whether the recommendation is provisional and why.

### Recommended workers

For each worker, show its name, task-specific assignment and constituent role primitives, selected model and reasoning effort, expected deliverable and completion condition, and typical and high token estimates. If exact model availability is unknown, give a provisional capability-based model choice and say that its identifier must be resolved. Specify independence, shared artifacts, and handoff order where relevant.

### Why this plan

Explain why one agent or the smallest useful team fits. Describe what a split would add and cost, or why there is no credible reason to split. Show an alternative only if it changes a meaningful tradeoff; include its workers, model and effort choices, deliverables, per-worker and total estimates, and the condition that would favor it.

### Usage and uncertainty

Show controller planning overhead separately from inclusive per-worker estimates, then the estimated plan total at typical and high usage. State the estimate source, included context, handoffs and retry assumptions, and uncertainty. Use the accounting rules in [usage estimation](../../../controller/usage-estimation.md). Label illustrative numbers and distinguish them from observed usage. Do not treat a high estimate as a guaranteed cap.

### Session implications

Give the allowance snapshot and its time, reservations for active workers, and what this plan would leave for other work under typical and high estimates. Keep token planning amounts separate from provider quota percentages. State reset times or mark them unknown. Explain dependencies, priority tradeoffs, and what happens if allowance is inadequate or unknown.

### Assumptions and escalation

List the assumptions that could change the choice, evidence that would justify stronger effort or another worker, and reasons to revise or stop. Identify which uncertainty needs investigation after dispatch rather than pretending it has already been resolved.

### Decision and edits

Restate the recommendation and its provisional conditions. Invite edits to the concrete proposal. Make clear that no workers have started and that edits require refreshed estimates before a separate execution decision.

See the complete [single-agent](../../../examples/single-agent.md) and [multiple-agent](../../../examples/multi-agent.md) proposals.
