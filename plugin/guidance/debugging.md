# Debugging guidance

Use this guide when an assignment starts from a defect or unexplained behavior. Inputs include symptoms, acceptance criteria, relevant code, and existing evidence. Output is a causal explanation, bounded fix proposal, and verification evidence.

Read the real entry point before selecting a cause. Reproduce the observable failure when feasible. Report any reproduction gap.

State a hypothesis and the observation that could reject it. Trace state and effects across the relevant boundary. Prefer a bounded experiment over repeated speculative edits.

Fix the demonstrated cause while preserving supported callers. Check the original symptom through the entry point after the change. Add failure cases when the cause implies broader exposure.

An exact error is evidence. Preserve its text and context. Distinguish a failed check from an unavailable environment.

For the locale defect, helper-level checks alone cannot show that the visible page updates without navigation. Observe the page behavior or report that evidence as unavailable.

Follow repository instructions and the common [engineering guide](engineering.md). [Source notes](../../docs/design-sources.md#writing-and-engineering) explain the adapted evidence principles.
