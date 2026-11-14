# Codex integration: desired versus unverified

This document separates product needs from claims about a future host. It uses the [interaction contract](../plugin/skills/propose/SKILL.md) and [scheduling needs](session-scheduling.md). Its result is an integration checklist for later investigation, not a statement that any Codex interface already supports these capabilities.

| Desired capability | Integration detail needing verification | Fallback for a proposal |
| --- | --- | --- |
| Discover and request a proposal | Exact invocation, skill discovery, and plugin loading conventions | Treat `/propose` as a working interaction name in prose |
| See task and session context | Access to task lists, priorities, dependencies, and repository context | Use user-supplied context and state assumptions |
| Choose model and effort per worker | Model discovery, permitted effort values, per-worker selection controls | Give provisional capability choices and unresolved identifiers |
| Observe allowance | Availability, scope, freshness, and reset semantics of quota information | Mark provider quota unknown; use a supplied token envelope if available |
| Account for usage | Reported token categories, tool usage, retries, and attribution to workers | Label predictions as estimates and record observation gaps |
| Prepare independent workers and handoffs | Isolation, parallelism, artifact sharing, and model controls | Describe assignments and dependencies without claiming execution |
| Preserve editable proposals and state | Supported review surface, persistence, and resumption behavior | Keep the proposal readable as Markdown |
| Execute a separately accepted setup | Dispatch authorization, cancellation, pausing, and event reporting | Leave execution unavailable until the boundary is verified |

No API, command syntax, model identifier, host quota conversion, or packaging layout is established here. Investigation of those details belongs to a later implementation phase. [Manifest outline](../plugin/manifest-outline.md) discusses possible package contents; [open decisions](../OPEN-QUESTIONS.md) captures the unresolved integration choices.
