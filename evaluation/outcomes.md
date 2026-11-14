# Outcomes and future evaluation

Evaluation compares predictions, observed costs, and accepted priority work. Inputs are original plans, pre-dispatch features, revisions, host observations, reports, acceptance decisions, and repairs.

Output is evidence for changing [estimation](../controller/usage-estimation.md), [selection](../controller/plan-selection.md), and [scheduling](../controller/session-scheduling.md). This scaffold performs no experiments or model training.

## Forecast quality

Preserve each original prediction with assignment, model, effort, source, assumptions, and time. Store revisions separately. Compare both initial totals and later remaining-work forecasts with subsequent observations.

Measure central forecast error, systematic bias, and observed range coverage. Group results by task difficulty, model, effort, assignment type, and available history. Report missing usage separately.

Assess experiment-heavy tasks by predicted outcome branches and their resulting work. Include inconclusive experiments, rejected approaches, repeated checks, and shared environment failures. Do not evaluate only successful paths.

Ranges are heuristic until evidence supports coverage claims. Cold-start results need their own report. Do not hide sparse-history failures inside aggregate results.

## Acceptance and total cost

Use the [outcome distinctions](../controller/task-assessment.md#distinct-outcomes-and-their-records). An ended turn, submitted report, passed check, and accepted task are different observations.

Track criterion-level evidence, user acceptance or rejection, unresolved gaps, and later repairs. Include manager usage, planning, messages, failed attempts, and all repair costs. Count costs beyond the original predicted repair scenario too.

For illustration, 10,000 initial task tokens plus 4,000 repair tokens consume 14,000 task tokens. Separately allocated planning costs must also be counted once. These values are invented.

Attribute delayed repairs to their originating task and the session where usage occurs. Do not charge the same session twice. Declare a follow-up window before comparing policies.

## Baselines and routing benefit

Compare complete policies under the same allowance, task stream, tools, starting information, reset schedule, and acceptance criteria. Charge planning and coordination overhead to every policy.

| Comparison | Question |
| --- | --- |
| One general developer, fixed available model and effort | Does routing complete more accepted priority work within the same allowance? |
| Same team and scheduler, fixed model and effort | Does model selection improve acceptance or reduce total repair-adjusted cost? |
| Same selection policy, simple priority queue | Does session scheduling improve dependency completion and protected priority work? |
| Historical estimation baseline versus separately trained predictor | Does prediction improve error and coverage on later, held-out work? |

Proposed defaults use user priority order and dependency readiness. Exact baseline models, effort, priority weights, and evaluation thresholds remain [open](../OPEN-QUESTIONS.md).

Begin with matched controlled sessions. Consider randomized comparable sessions when execution is authorized. Report accepted priority work, failed or deferred work, budget overshoot, repair-adjusted cost, elapsed time, and uncertainty.

Keep acceptance criteria stable across policies and delegation. A policy cannot improve its result by shrinking required behavior or redefining priorities.

Historical replay cannot establish outcomes for untried models or teams. Use it for prediction checks and hypothesis generation. Keep revisions of one task together in held-out evaluation.

Pre-dispatch predictor inputs must predate dispatch. Evaluate revised remaining-work forecasts against their own information cutoff.

Storage format, retention, predictor architecture, sample size, repair window, and adoption thresholds remain unresolved. No training-data requirement is asserted here.
