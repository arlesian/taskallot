# Start or resume a selected plan

`/setup-agents` is a working product name. See [integration evidence](../../../controller/codex-integration.md) for actual host conventions.

This skill takes a selected [plan revision](../../../controller/plan-format.md) and an optional run reference. It uses [lifecycle state](../../../controller/agent-lifecycle.md), [budget policy](../../../controller/session-scheduling.md), and the [writing profile](../../guidance/writing.md).

## Validation and result

Validate configuration, acceptance criteria, reporting relationships, edit scopes, and dependencies. Refresh model availability, allowance observations, and stale estimates. Resolve provisional model labels before dispatch. Do not silently substitute an explicit user model choice.

For a fresh launch, create a run and record its authorization envelope. For resumption, reconcile the selected revision with the existing run. Follow the lifecycle's duplicate-prevention rules before dispatching ready assignments.

Repeated setup for the same selected plan must inspect matching runs first. Return existing activity or completion when appropriate. Require an explicit fresh-run choice before intentionally repeating completed work. Report ambiguous matches without launching another copy.

Report started, waiting, blocked, and failed startup items with their references. Keep successful launches recorded after partial failure. A retry reconciles those launches instead of restarting all agents.

## Authorization boundary

Require clear user intent to start or resume the selected plan. Skill discovery and plan editing do not grant execution authority.

Starting a selected plan authorizes its assignments and bounded follow-up work under its recorded rules. Normal handoffs, dependent work, and in-scope retries need no repeated user confirmation.

User input is required for expanded outcomes, weaker acceptance criteria, broader edit authority, or spending beyond the authorized envelope. Unapproved additional agents or external actions also exceed that envelope.

A manager can request an in-scope follow-up. The controller checks policy and records it before dispatch. Without a manager, the controller advances only predefined work and retries. It cannot supply missing engineering judgment.

The output states fresh launch or resume, run and revision references, agent states, reservations, and material gaps. Use the compact [proposal fields](../propose/SKILL.md) for revised setup decisions. Host permission requirements still apply independently.
