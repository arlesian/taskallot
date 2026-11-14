# Outcomes and later evaluation

Evaluation asks whether estimates are useful and whether routing completes more priority work within the same allowance. It uses saved proposals, pre-dispatch features, observed usage where available, acceptance decisions, and subsequent repairs. Its result is evidence for changing estimation, selection, and scheduling policies, not an implementation in this scaffold.

## Prediction accuracy

Retain the original task, assignment, model and effort, estimate source, typical and high predictions, planning overhead, and allowance snapshot. Later observations should distinguish controller usage, each worker's usage, handoffs, retries, and repair work. Attribute delayed repairs to the originating task as well as the session in which they consume allowance; do not charge a session twice. Storage and retention are [open decisions](../OPEN-QUESTIONS.md).

Compare typical predictions with observed totals for systematic over- or underestimation and error magnitude. Check how often observations exceed high estimates and by how much, grouped by task characteristics, model, effort, and history available at prediction time. High estimates are scenarios until evidence supports a calibrated interpretation. Unknown token categories remain gaps; quota percentage changes are not substitute token measurements.

Compare a later separately trained predictor with the historical baseline on held-out, later work. Keep revisions of the same task together and use only features available before dispatch. Report cold-start performance separately so abundant-history results do not hide weak early estimates. [Usage estimation](../controller/usage-estimation.md) owns prediction inputs and accounting rules.

## Acceptance and repairs

Track whether the task's acceptance conditions were met, what evidence supports that decision, any unresolved gaps, user rejection, and later regressions or repairs. Worker completion, a passing check, and user acceptance are distinct outcomes. Include unsuccessful attempts and abandoned work in consumed allowance. Record initial acceptance separately from acceptance that required repair, and count all usage through a declared follow-up window.

For illustration only, an initially accepted patch using 10,000 tokens followed by a 4,000-token repair consumes 14,000 task tokens, plus any separately recorded controller overhead. It must not remain a 10,000-token success in policy comparisons. These quantities are invented.

## Routing policy comparison

Use a simple baseline: one general coding worker per task at a fixed available model and effort, taking ready tasks in user priority order with a dependency tie-break. Exact model, effort, and tie-break remain proposed choices. Give baseline and proposed policy the same task stream, allowance, starting information, tools, reset schedule, and acceptance criteria. Charge planning overhead, failed attempts, and repairs to both.

Begin with matched controlled sessions, then consider randomized comparable sessions when execution is available. Evaluate accepted priority work within the allowance after the repair window, alongside quota overruns, deferred or unfinished priority tasks, acceptance quality, and elapsed time. Keep the task priority scheme fixed across policies; a policy must not improve its score by redefining priorities or shrinking acceptance conditions. Repeat across task mixes and allowance sizes and report uncertainty rather than treating a small sample as proof.

Historical replay alone cannot establish routing benefit: it lacks outcomes for workers and models that were never tried. Use it for hypothesis generation and prediction checks. Decisions about priority weighting, sample size, repair window, and an improvement threshold belong in [open decisions](../OPEN-QUESTIONS.md).
