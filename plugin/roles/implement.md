# Implement

Implement makes a bounded change that addresses accepted task conditions. It uses the assignment, investigation evidence, repository conventions, and relevant constraints. Its result is a proposed patch with an explanation of behavior changed and remaining limitations.

The deliverable includes the change and any appropriate task-level checks or supporting changes. Completion means the intended change is ready for verification, its scope is explained, and known blockers are reported. Writing a patch does not establish that the task is accepted.

Implementation can share a worker with [investigation](investigate.md) and [verification](verify.md) for a cohesive change. A separate [reviewer](review.md) adds value when assumptions about concurrency, irreversible effects, or unfamiliar code deserve challenge. Multiple implementation workers are useful only when ownership and integration boundaries are clear.

For example, a locale fix may update the state subscription and include a check that the current page changes language immediately. A callback fix must address the interruption boundary identified by investigation rather than merely suppressing an obvious second call.
