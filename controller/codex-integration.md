# Codex integration evidence

TaskAllot proposes a small local controller connected to Codex's documented app-server surface. This document separates required capabilities, documentary evidence, and future prototype work.

Use the [shared vocabulary](task-assessment.md). [Lifecycle](agent-lifecycle.md) owns recovery policy. [Plan format](plan-format.md) owns configuration authority.

## Evidence status

Research date: 2026-11-14. Official documentation was read on that date. Documentation can describe a different version from the installed CLI.

Local inspection found Codex CLI 0.169.0. Only version reporting and app-server help were exercised. The installed help labels app-server experimental and lists transport options. No server, agent, turn, or prototype was started.

“Documented” means an official source describes the capability. It does not mean TaskAllot tested it here. Every runtime mapping below still needs a compatibility prototype for the selected host version.

## Skill names and host conflicts

[Official skill documentation](https://developers.openai.com/codex/skills) describes explicit `$skill` references. Skill discovery does not establish that arbitrary slash commands become available.

[Official command documentation](https://developers.openai.com/codex/cli/slash-commands) includes host `/plan` and `/status` commands. The five TaskAllot slash-style names remain product labels. Check the target surface for other conflicts before packaging.

Proposed naming option: `taskallot-propose`, `taskallot-plan`, `taskallot-setup-agents`, `taskallot-agents`, and `taskallot-status`. An explicit reference could use `$taskallot-plan` after registration is verified. Do not promise `/taskallot-plan` syntax.

Prototype discovery, explicit invocation, and start authorization separately. Fallback: request the named TaskAllot action in ordinary text and return a descriptive response. No action is installed by this scaffold.

## Capability evidence and fallback

All rows share the research date above. Unless stated otherwise, evidence is documentation only; runtime behavior was not tested here.

| Required capability | Official support read | Future prototype must establish | Fallback |
| --- | --- | --- | --- |
| Model discovery | App-server `model/list` exposes models and effort options. [Source](https://developers.openai.com/codex/app-server) | Account availability, pagination, supported settings, and version compatibility | Provisional capability choices; block dispatch until resolved |
| Agent context creation and resumption | `thread/start`, `thread/resume`, and `thread/read` are documented. [Source](https://developers.openai.com/codex/app-server) | Durable run mappings and recovery after lost replies | Keep uncertain assignments blocked; inspect host records |
| Assignment dispatch and setting changes | `turn/start` accepts model and effort. [Source](https://developers.openai.com/codex/app-server) | Safe boundaries, setting persistence, and authorization mapping | New context with a bounded handoff, or no dispatch |
| Interruption | `turn/interrupt` and interrupted turn status are documented. [Source](https://developers.openai.com/codex/app-server) | Cancellation latency and effects already committed | Stop new dispatch; reconcile current effects |
| Activity and completed turns | Turn and item notifications are documented. [Source](https://developers.openai.com/codex/app-server) | Reconnect, missing-event recovery, deduplication, and milestone mapping | Re-read stored host state; mark stale activity |
| Usage attribution | `thread/tokenUsage/updated` is documented. [Source](https://developers.openai.com/codex/app-server) | Category containment, cumulative semantics, tool and child costs, and missing data | Show observed scope and unknown gaps; reserve uncertainty |
| Provider observations | `account/rateLimits/read` and updates expose scoped percentages and resets. [Source](https://developers.openai.com/codex/app-server) | Authentication coverage, bucket scope, freshness, and availability | Provider allowance unknown; retain separate session budget |
| Nested worker control and visibility | Configuration lists spawned-thread limits. [Source](https://developers.openai.com/codex/config-reference) | Prevention of unmanaged delegation and complete child usage attribution | Disable autonomous nested execution; show managed or attached agents only |
| Filesystem and tool authority | App-server documents sandbox and approval settings. [Source](https://developers.openai.com/codex/app-server) | Assignment scope mapped to enforceable host restrictions | Restrict the run to supported authority; report unsupported controls |
| Native terminal presentation | `tui.status_line` configures footer items. [Source](https://developers.openai.com/codex/config-reference) | Whether custom TaskAllot fields or panels can integrate | Separate [terminal pane](../interface/terminal-monitor.md) |

No exact token conversion from quota percentages was verified. No hard session-wide cutoff, exactly-once dispatch guarantee, or complete host-agent discovery was verified.

Role prose and repository `AGENTS.md` do not create runtime controls. Registration, permission enforcement, durable controller storage, and monitor integration remain future work.

[Design sources](../docs/design-sources.md) records the broader patterns. [Open decisions](../OPEN-QUESTIONS.md) lists consequential choices and proposed defaults.
