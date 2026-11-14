# Investigate

Investigate turns uncertainty about a task into evidence usable for a decision or change. It uses the task's acceptance conditions, supplied symptoms, accessible source and existing diagnostic evidence. It owns tracing causes and boundaries, not selecting the session budget policy.

The deliverable is a concise explanation of the likely cause, supporting locations or observations, unresolved alternatives, and implications for implementation and verification. It is complete when the next action has an evidence-backed basis, or when a specific blocker and the evidence needed to resolve it are reported. Certainty is not required; an unsupported guess is insufficient.

Investigation can share a worker with [implementation](implement.md) and [verification](verify.md) when the same context is useful and the work is tightly coupled. Independence adds value when another worker can challenge a high-impact assumption without inheriting the first worker's conclusion.

For example, tracing why locale changes appear only after navigation can lead directly to a small state-update fix. For duplicate essay scoring, a separate investigator can derive callback interruption sequences while the implementation worker traces the current flow. [Task assessment](../../controller/task-assessment.md) defines how roles compose into an assignment.
