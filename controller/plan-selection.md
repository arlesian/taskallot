# Plan selection

Selection recommends an agent setup from the [task brief](task-assessment.md), available models and reasoning efforts, [pre-dispatch estimates](usage-estimation.md), and [session constraints](session-scheduling.md). Its result is one justified plan in the [proposal format](../plugin/skills/propose/SKILL.md).

Consider a one-agent plan first. When there is a credible benefit from parallel work, independent judgment, or distinct expertise, compare it with the smallest useful team. Describe the specific benefit and include duplicated context, coordination, integration, and repair exposure in the estimate. Do not split work merely because several roles are present. A second worker needs a bounded deliverable that can affect acceptance.

Choose a model and effort for each assignment using difficulty, uncertainty, likely benefit from stronger reasoning, and session allowance. A difficult but tightly coupled bug may call for one strong model at high effort. A narrower independent verification assignment may suit a less costly model at medium effort. A second worker can add independent reasoning even when increasing the first worker's effort would not. Stronger reasoning is not assumed to improve every task.

Use actual supported model identifiers and effort settings when verified. With missing availability, recommend provisional capability tiers and efforts and flag that they need resolution; do not claim that a named model exists or that a tier has a known price. Model mappings and effort policy are [open decisions](../OPEN-QUESTIONS.md).

Weigh expected acceptance and repair risk against total usage while protecting higher-priority session work. Prefer a cheaper plan when extra usage offers no credible benefit. Consider elapsed time when the user values it, but do not treat parallel execution as token savings. There is no fixed team-size score, difficulty threshold, or escalation multiplier yet.

Recommend one plan. Show another only when it changes a meaningful tradeoff, such as independent failure analysis versus preserving allowance. If no credible plan fits, explain a narrower scope or deferral instead of silently removing required verification.

For the locale symptom, shared causal context can make one worker sufficient. For duplicate scoring, independently deriving interruption cases can expose an assumption shared by the patch and its author's checks. The [examples](../examples/multi-agent.md) show that benefit and the tighter-budget alternative.
