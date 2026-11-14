# Single-agent proposal: locale update

This example follows the [canonical format](../plugin/skills/propose/SKILL.md). All token amounts, allowance snapshots, and model capabilities below are illustrative assumptions, not measurements or verified availability.

## Task and context

A language selector updates the visible page only after navigating away and back. Acceptance requires the selected language to appear on the current page without navigation and remain correct after later navigation. Existing language selection behavior should still work.

This is provisionally a moderately difficult, tightly coupled state propagation problem. No source has been inspected; a missing subscription is only one possible cause. Assume balanced and strong coding models with medium and high effort are available. A later urgent migration check is independent and needs a protected high estimate of 12,000 tokens. Its priority is higher, but its required input is not ready yet.

## Recommended workers

| Worker | Assignment and role primitives | Model and effort | Deliverable and completion | Typical tokens | High tokens |
| --- | --- | --- | --- | --- | --- |
| Locale worker | Trace the locale update, implement the fix, and verify it without navigation; investigate, implement, verify | Balanced coding model, medium effort; actual identifier unverified | Causal explanation, bounded patch, and evidence for immediate and post-navigation updates; complete when conditions are evidenced or a blocker is reported | 8,000 | 16,000 |

The same worker owns diagnosis, change, and checks, reusing the locale flow context. No independent review or worker handoff is proposed.

## Why this plan

One agent can follow the state update to its consumer and check the resulting behavior in the same context. There is no current evidence of separable work or a failure boundary that needs a fresh interpretation. A second worker would duplicate context before it offered a clear acceptance benefit. No alternative is shown because the task description provides no meaningful reason to split.

## Usage and uncertainty

| Component | Typical tokens | High tokens |
| --- | --- | --- |
| Controller planning and proposal | 2,000 | 4,000 |
| Locale worker, inclusive | 8,000 | 16,000 |
| Estimated plan total | 10,000 | 20,000 |

These are cold-start heuristic scenarios using only the symptom, assumed local scope, and expected checks. Worker usage includes supplied context, diagnosis, patch, verification, and final report. There are no handoff charges. Typical assumes a focused fix with routine iteration; high allows a broader trace and one bounded repair and recheck. A cross-system localization redesign is outside both scenarios. Uncertainty is substantial, and high is not a cap.

## Session implications

At planning start, assume a user-supplied remaining token envelope of 40,000 and high remaining reservations of 6,000 for other active work. That leaves 34,000 before this proposal's plan. Provider quota percentage and reset time are unknown.

After existing reservations and this plan, 24,000 tokens remain in the typical scenario and 14,000 in the high scenario. Both preserve the migration check's 12,000 high estimate, leaving 12,000 or 2,000 for other unstarted work. These are token planning amounts, not inferred provider capacity. Planning overhead is included from the snapshot and must be reconciled once as actual usage becomes known. If the migration input becomes ready, scheduling must reconsider its higher priority before dispatch.

## Assumptions and escalation

Assume a local state or rendering issue and an environment where the visible behavior can be checked. A translation service defect, cross-process cache, or inability to observe the page changes scope and weakens these estimates. Escalate to a strong model at high effort if tracing reveals difficult coupled state transitions; consider another worker only if a distinct independent question appears. Re-estimate before adding work, especially if it would consume the migration reservation. Missing execution evidence must be reported as a gap.

## Decision and edits

Recommend the single locale worker provisionally, subject to model availability and confirmation of the session snapshot. No workers have started. The user can edit the scope, assignment, effort, or protected later work; refresh affected estimates and session implications before a separate execution decision.
