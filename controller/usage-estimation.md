# Pre-dispatch usage estimation

This component predicts tokens for a specific task, candidate model, reasoning effort, and assignment before that worker starts. It supplies comparable estimates to [plan selection](plan-selection.md) and reservations to [session scheduling](session-scheduling.md). It does not choose the team or translate provider quota percentages into tokens.

## Available evidence

Use the task brief, proposed roles and deliverables, context expected to be passed, known repository scale, required checks, dependencies, and prior completed assignments available at prediction time. Model and effort are inputs, not labels applied after estimating. Exclude future worker discoveries, final patch size, actual retries, and eventual acceptance from prediction inputs. Such observations can become outcomes for later evaluation.

## Historical baseline and cold start

Start with a simple historical baseline using comparable assignments, grouped by model and effort and broad task, context, and role characteristics. The proposed default is a central historical value for typical usage and an upper historical range for high usage, with similarity and sample count disclosed. Exact statistics, grouping boundaries, and minimum history are [open decisions](../OPEN-QUESTIONS.md).

With sparse or no history, widen comparisons to less similar work and disclose the loss of relevance. If none exists, give a rough scenario-based range from expected context, work, checks, and possible repair, label it heuristic, and avoid numerical confidence claims. Do not invent observations or give false precision. A recommendation can remain provisional even when usage cannot be credibly quantified.

Later, evaluate a separately trained predictor against this baseline. Train it on recorded pre-dispatch features and subsequent outcomes; do not substitute the proposing model's unsupported numerical guess for a trained predictor. Model family, training method, minimum data, and storage format remain undecided. [Evaluation](../evaluation/outcomes.md) owns comparison and calibration.

## Accounting boundary

Report controller planning overhead separately, including assessment, candidate comparison, proposal generation, and anticipated revision work. Worker estimates include input context, reasoning and output where applicable, tool-result context, checks, and the modeled allowance for retries or repair. Count tokens according to the selected model's reported categories when known; disclose unavailable categories rather than claim full visibility.

Charge handoff production to its sender and handoff input to its recipient. They are distinct token uses. Repeated context in later calls consumes usage again; avoid adding a second blanket context charge to an already inclusive worker estimate. Include a separate integration worker only if proposed; otherwise assign integration to a named worker. Comparing alternatives adds controller work, not execution costs for workers that will never run.

Typical means a plausible central outcome, including ordinary retry exposure when supported by history. High means a conservative scenario with more exploration, context, or repair. It is not a guaranteed cap or a calibrated percentile without evidence. State the retry scope; neither estimate covers unlimited repairs.

The plan total combines controller overhead and all recommended workers. Sum high estimates as a conservative scenario, not as a claim about a joint confidence level. Reconcile already incurred planning usage at the allowance snapshot so it is never charged twice. Prediction revisions describe additional expected usage and preserve the original estimate for evaluation.

For example, widening a locale assignment from tracing page state to investigating a distributed translation cache changes its prediction even at the same model and effort. The [single-agent example](../examples/single-agent.md) demonstrates the accounting with explicitly illustrative quantities.
