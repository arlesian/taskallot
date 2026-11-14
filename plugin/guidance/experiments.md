# Bounded experiment guidance

Use an experiment when evidence could change the coding approach. Inputs include a hypothesis, comparable baseline, task criteria, environment, and execution allowance. Output is an observation and a next decision.

| Field | Required description |
| --- | --- |
| Hypothesis | The claim and an observation that could reject it. |
| Comparison | Baseline and candidate under comparable conditions. |
| Acceptance measure | Observable threshold or required behavior, specified before observing results. |
| Execution budget | Allowed attempts, token range, time or tool limits, and stop condition. |
| Outcomes | At least the useful success, rejection, and inconclusive paths when each is credible. |
| Next decision | Work retained, removed, or added under each outcome. |

Separate measured results from predicted benefits. Record environment, artifacts, and limitations so another agent can interpret the result.

Do not turn an inconclusive result into success. Do not repeat experiments beyond the assignment's bounds. Request a revised estimate when evidence changes remaining work.

The [experiment example](../../examples/experiment.md) preserves its initial estimate and records an outcome-based revision. [Estimation](../../controller/usage-estimation.md) owns forecast accounting. Repository instructions and [engineering guidance](engineering.md) still apply.
