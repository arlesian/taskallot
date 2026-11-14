# Task assessment

Assessment converts the task description and available session context into acceptance conditions and planning constraints. Its result is a task brief for [plan selection](plan-selection.md) and [usage estimation](usage-estimation.md), with evidence separated from assumptions.

## Vocabulary

A role is a responsibility primitive with a deliverable and completion condition: [investigate](../plugin/roles/investigate.md), [implement](../plugin/roles/implement.md), [verify](../plugin/roles/verify.md), or [review](../plugin/roles/review.md). These are the four fixed primitives in this design. Future additions are possible through an explicit vocabulary revision.

An agent, also called a worker, is one proposed execution participant with a selected model and reasoning effort. An assignment is that worker's task-specific work, composed from one or more role primitives. An assignment label can vary without creating a new primitive. A plan combines workers, assignments, dependencies, estimates, and session implications. A team contains more than one worker; four roles do not require four agents. The controller prepares proposals and schedules; its usage is accounted for separately from workers.

## Inputs and result

Use the requested behavior, acceptance evidence, repository context already available, likely scope and difficulty, uncertainty, coupling, risk of failure, and opportunities for independent work. Include available models and efforts, allowance information, and other session tasks with their priorities and dependencies. Unknown inputs stay unknown. Explicit user priorities outrank inferred ones.

Assess before dispatch. Source inspection by future workers is not evidence already available to the proposal. With only a symptom description, infer a provisional scope, name its assumptions, and identify what would change the brief. Do not invent a root cause or require a preliminary worker just to provide a recommendation.

For the locale symptom, a possible acceptance condition is that selecting another language updates the current page without navigation and continues to work after navigation. A proposed assignment can be “trace the locale update, implement the fix, and verify it without navigation,” combining three roles in one agent. Whether that scope is truly local remains an assumption until investigated.
