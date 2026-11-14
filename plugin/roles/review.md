# Review

Review challenges whether a proposed change and its evidence are sufficient. It uses the task conditions, patch, investigation notes, and verification results. Its result is a prioritized assessment of correctness risks, maintainability concerns, missing evidence, and acceptable tradeoffs.

The deliverable gives actionable findings with reasons, or states that no blocking findings were identified and names the review's limits. Completion means the agreed scope has been assessed and blockers are clear. A completed review with blocking findings does not mean the task is accepted; findings need repair or an explicit disposition.

Review can share a worker with [verification](verify.md) because observed failures inform critique. An implementer may perform self-review, but the proposal must not label that independent review. A separate worker is useful when a fresh interpretation of the requirements or failure boundary could change the answer.

For example, an independent reviewer of duplicate scoring can question whether the fix survives an interruption after recording a score but before acknowledging the callback. More workers are not inherently better; [plan selection](../../controller/plan-selection.md) weighs that benefit against cost.
