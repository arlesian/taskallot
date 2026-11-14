# Setup and model selection

Selection recommends one setup from the [task brief](task-assessment.md), user preferences, supported model settings, [estimates](usage-estimation.md), and [session policy](session-scheduling.md).

Its output uses the compact [proposal format](../plugin/skills/propose/SKILL.md). It does not launch agents.

## Team and role choice

Consider one developer first for a cohesive task. Diagnosis, implementation, and self-checks can share context without creating separate job profiles.

Compare the smallest useful team when independent assessment, separable experiments, or clear parallel ownership can improve the outcome. Include duplicated context, management, handoffs, integration, and repair in its cost.

A dedicated manager is optional for small single-agent work. Use one when reports, dependencies, and follow-ups require coordination. Count manager usage explicitly.

Recommend one setup. Show an alternative only when it changes a material tradeoff. For example, removing an independent auditor saves usage but reduces independent failure analysis.

## Model and effort choice

Choose each agent's settings using task difficulty, uncertainty, expected acceptance, likely repair exposure, and remaining allowance. Prefer a cheaper setup when extra usage provides no credible benefit.

A difficult but tightly coupled defect may need one strong developer. Independent review can justify another reasoning context even when stronger developer effort cannot replace that independence.

Low allowance does not automatically imply a weaker model. A critical difficult task can justify preserving a strong model and deferring lower-priority work. A routine bounded audit can use a less costly model when it can assess the criteria adequately.

Use verified model identifiers and supported efforts before dispatch. Capability labels are provisional when availability is unknown. Do not override explicit user selections silently.

Do not treat parallel execution as token savings. Consider elapsed time only when it supports the user's priorities. Selection thresholds and model mappings remain [open](../OPEN-QUESTIONS.md).

If no credible setup fits, propose deferral, a narrower accepted scope, or bounded investigation. Do not silently drop required checks or weaken acceptance.
