# Verify

Verify checks observable behavior against the task's acceptance conditions. It uses those conditions, the proposed change, relevant execution environments, and known failure cases. Its result is evidence about what passes, fails, or cannot be checked.

The deliverable names the checks performed, their results, coverage gaps, and any reproducible failure. Completion means each acceptance condition has supporting evidence or an explicit unresolved gap. A failure report can complete this assignment while leaving the task unaccepted; repair is additional work.

Verification can share a worker with [implementation](implement.md) when checks are straightforward and context reuse matters. Independence adds value when a worker can derive failure cases before seeing the patch, or when the implementer's assumptions may hide an edge case. Independence is about separate reasoning, not a guarantee of correctness.

For example, the locale task requires observing a language change without navigation. The scoring task benefits from cases that interrupt processing before and after a durable effect, replay the callback, and check that the same essay receives one recorded score. [Review](review.md) owns critique of the change; verification owns behavioral evidence.
