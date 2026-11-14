# Review and audit guidance

Use this guide when assessing a change or its behavior. Inputs include criteria, source and patch context, checked artifact revision, and available results. Output is evidence and actionable findings.

An auditor checks observable behavior. A reviewer assesses correctness, design, maintainability, and relevant concurrency risks. Use the [job profiles](../roles/auditor.md) and [shared vocabulary](../../controller/task-assessment.md) for their authority.

Check design fit and supported caller behavior. Examine failure boundaries and unnecessary complexity. Prefer concrete defects over speculative abstraction preferences.

Tie each finding to a location, reason, consequence, and checked revision. Separate blocking defects from optional improvements. State passed, failed, and unavailable checks accurately.

Judge tests by the behavior they protect. A useful check fails when required behavior breaks and survives an internal refactor that preserves behavior.

Inspect the real entry point when the requirement depends on it. A passing helper check cannot establish an unobserved user-visible result.

After repair, identify the new artifact and repeat affected checks. Preserve old reports as history. A clean review does not remove evidence gaps.

These principles adapt [Google and pstack guidance](../../docs/design-sources.md#writing-and-engineering). Follow repository instructions and the [writing profile](writing.md).
