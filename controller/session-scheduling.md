# Session scheduling

Scheduling allocates attention and allowance across all known session work, not just the latest task. It uses remaining tasks, priority, dependencies, acceptance state, active workers, reservation estimates, allowance snapshots, and known quota reset times. Its result is a proposed next assignment and a revised session outlook; dispatch remains subject to the [proposal interaction](../plugin/skills/propose/SKILL.md).

## Allowance and reservations

Track predicted and observed tokens in a token planning ledger. Keep provider-reported quota percentages, their scope, observation time, and reset time separately. A user-supplied token envelope can guide planning, but is not a provider guarantee. Do not convert percentages to token counts without a verified provider mapping. Missing quota information or reset times are unknown, never zero or unlimited.

Reserve for active workers before offering allowance to new work. Proposed default: use each active assignment's high estimate of remaining usage; update it from observed progress rather than repeatedly reserving its original total. Pending proposals show hypothetical reservations. Deduct actual usage once, release unused reservations when a worker finishes, and replace reservations when revising rather than stacking old and new totals. Already spent planning tokens need the same reconciliation.

Protect known higher-priority work, including work that becomes actionable only after dependencies finish. Choose among ready tasks using priority and dependency effects, then assess feasible plans with the allowance left after reservations. Reset times may make deferral useful, but only a confirmed reset with a known scope can replenish that scope. Unknown allowance supports a conditional proposal, not an assertion that it fits. Reservation margins and priority tie-breaking remain [open decisions](../OPEN-QUESTIONS.md).

## Session tradeoffs

Spending more now can help the whole session: a shared authentication failure might block several priority fixes. One stronger worker that reliably removes the blocker may preserve more downstream work than repeated cheap attempts. Include this dependency benefit when comparing plans.

Preserving allowance can be better: a small locale display defect with low coupling may need only one capable worker, leaving room for a later urgent migration check. Independent review of the locale patch may add less value than protecting that later task. These are planning judgments, not measured performance claims.

## Revision after events

After an overrun, replace the affected worker's remaining estimate, retain spent usage, and recheck reservations and future tasks. Propose a narrower next step, deferral, or stronger model only if its benefit still fits; do not keep retrying on the old budget.

After failure, use the failure evidence to distinguish repair, renewed investigation, and a blocked acceptance condition. Estimate additional work separately and update the recommendation. Worker completion is not necessarily task acceptance, as [evaluation](../evaluation/outcomes.md) explains.

When a new task arrives or priorities change, reassess ready work and dependencies. Avoid treating reserved active work as free allowance. Propose finishing, pausing, or changing active work where the host permits it, identify sunk and duplicated costs, and refresh the user's proposal. An event does not itself authorize another worker or automatic replacement execution.
