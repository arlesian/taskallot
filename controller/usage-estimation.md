# Uncertainty-aware usage estimation

This component predicts usage before dispatch for each candidate task, assignment, model, and effort. It supplies [selection](plan-selection.md), [scheduling](session-scheduling.md), and the [plan record](plan-format.md).

Use the [shared vocabulary](task-assessment.md). Prediction does not dispatch work or convert provider quota percentages into tokens.

## Prediction record

| Field | Meaning |
| --- | --- |
| Candidate | Task, assignment scope, agent roles, model, effort, and expected deliverables. |
| Central estimate | Plausible expected usage under stated assumptions; a heuristic central scenario when history is insufficient. |
| Plausible range | Lower and upper scenarios, with their scope and uncertainty. Neither bound guarantees an outcome. |
| Source | Comparable historical assignments, sample count, similarity limits, or an explicit cold-start heuristic. |
| Assumptions | Context size, environment, checks, experiment outcomes, handoffs, and failure boundaries. |
| Retry exposure | Bounded attempts, repairs, rechecks, and stopping conditions included in the estimate. |
| Freshness | Prediction time, plan revision, source availability, and changes that require re-estimation. |

Inputs must exist before dispatch. Use supplied symptoms, known repository context, required checks, expected tool output, assignment boundaries, and comparable history. Exclude the candidate assignment's eventual patch size, discoveries, actual retries, and acceptance outcomes.

Estimates depend on model and effort. A new assignment scope needs a new estimate even when the agent remains the same.

## Baseline, cold start, and later prediction

Start with comparable historical assignments grouped by model, effort, context, and broad work type. Proposed default: use a central historical value and conservative observed ranges. Exact statistics and similarity boundaries remain [open](../OPEN-QUESTIONS.md).

With sparse history, disclose weaker comparisons and wider uncertainty. With no useful history, use clearly labeled heuristic scenarios. Do not fabricate measurements, outcome probabilities, percentiles, or training-data requirements.

Later, compare a separately trained predictor with the simple baseline. Use recorded pre-dispatch features and subsequent outcomes. Architecture, training method, storage engine, and adoption thresholds remain undecided. [Evaluation](../evaluation/outcomes.md) owns calibration and comparison.

## Experiments and changing work

Describe credible outcomes before running an experiment. Each outcome can change implementation, checks, and remaining usage. Do not assume the experiment succeeds merely because its own execution is cheap.

For example, cache trials can support the candidate, reject it, or expose unstable measurements. The [experiment example](../examples/experiment.md) shows all three paths and an outcome-based revision.

Preserve the original estimate. Store revisions separately with new evidence, changed assumptions, and prediction time. Do not replace a poor forecast with the eventual observation.

Revised forecasts can use evidence available at their revision time. Keep that later evidence out of the original pre-dispatch feature record.

## Inclusive accounting

Count planning model calls separately from agent assignments. A manager is an agent: include its coordination, reading, messaging, reporting, and resumption usage explicitly.

Each assignment estimate includes input context, reasoning and output where reported, tool-output context, message production and consumption, checks, and reporting. Include bounded retries and repair exposure once.

Charge handoff production to its sender and consumption to its recipient. Repeated context can consume tokens again. Do not add blanket context or messaging charges to already inclusive assignment estimates.

The deterministic controller and monitor do not inherently consume model tokens. Any model-assisted summarization or assessment is a named, accounted call. Routine status refresh needs none.

Use provider totals and category relationships when known. Cached input can already be included in input tokens. Reasoning can already be included in output tokens. Do not add a child category to its reported parent again.

Do not sum cumulative usage updates as independent charges. Reconcile them by host reference and observation scope. Missing categories or delayed usage remain unknown. Do not infer them from quota percentage changes.

## Active and aggregate forecasts

| Value | Meaning |
| --- | --- |
| Observed usage | Confirmed usage already incurred, with scope and freshness. |
| Remaining estimate | Central value and range for work still required. |
| Forecast total | Observed usage plus estimated remaining usage, with observation gaps disclosed. |

Revisions update remaining work. They retain observed costs and original predictions. Failure does not erase consumed tokens.

Aggregate assignments by task using stable references. Allocate shared planning or manager costs once, and identify the allocation rule. Task totals include failed attempts and repairs. Session totals must not count the same shared cost again.

Shared failures can affect several agents. An unavailable environment can force both a developer and auditor to repeat work. Include credible shared-failure scenarios at task or plan level.

Summing individual upper estimates gives a planning scenario, not a calibrated plan-level percentile. Claim coverage only after evaluation establishes it for comparable work.
