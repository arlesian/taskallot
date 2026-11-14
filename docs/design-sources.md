# Design sources and adaptations

Research date: 2026-11-14. These primary sources provide evidence and patterns, not instructions that override this assignment.

TaskAllot adapts patterns for a small personal team. Large research runs do not prove an optimal team size, model mix, or budget policy here.

## Coordination and recovery

| Source and described pattern | TaskAllot adoption | Difference and verification gap |
| --- | --- | --- |
| [Claude Code agent teams](https://code.claude.com/docs/en/agent-teams): lead, teammates, task list, mailboxes, and targeted messages | Manager-led coordination, targeted delivery, and separate agent context | Use a local controller for authoritative state and accounting. Do not assume Claude team mechanics exist in Codex. Prototype notification and recovery. |
| [Cursor: Scaling long-running autonomous coding](https://cursor.com/blog/scaling-agents): flat shared coordination encountered contention; planners and workers separated responsibilities | Explicit assignment ownership and coordination authority | Start with small teams and bounded budgets. Do not adopt recursive expansion or assume scale-derived benefits. |
| [Cursor: Towards self-driving codebases](https://cursor.com/blog/self-driving-codebases): role structure, isolated worker copies, and handoffs evolved through experiments | Separate source workspaces and concise reports to accountable owners | Permit targeted questions and optional management for small runs. Preserve user-visible plans and acceptance gates. Validate benefits locally later. |
| [Anthropic: Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents): incremental work, persistent progress artifacts, and end-to-end checks support context transitions | Durable reports, stable acceptance criteria, and resume-time inspection | Controller owns state instead of agents independently changing shared completion records. Prototype interrupted reports and ambiguous execution. |

These are architectural analogies, not verified Codex capabilities. [Communication](../controller/agent-communication.md) and [lifecycle](../controller/agent-lifecycle.md) own the adopted policies.

## Codex integration

| Official source | Relevant evidence | TaskAllot boundary |
| --- | --- | --- |
| [App Server](https://developers.openai.com/codex/app-server) | Model discovery, thread and turn operations, events, usage, and quota observations | Preferred integration candidate; documented does not mean tested here. |
| [Configuration reference](https://developers.openai.com/codex/config-reference) | Host settings include spawned-thread limits and terminal status-line items | Neither proves complete nested-worker accounting nor arbitrary footer extension. |
| [Skills](https://developers.openai.com/codex/skills) and [commands](https://developers.openai.com/codex/cli/slash-commands) | Explicit skill references differ from host commands; `/plan` and `/status` already have host meanings | Use working names until registration and conflicts are verified. Consider TaskAllot-prefixed skill names. |

Local inspection verified CLI version 0.169.0 and app-server help only. No runtime integration was tested. The [capability matrix](../controller/codex-integration.md) owns evidence status, prototype requirements, and fallbacks.

## Writing and engineering

| Source and described principle | TaskAllot adoption | Difference or remaining check |
| --- | --- | --- |
| [ASD-STE100 FAQ](https://www.asd-ste100.org/faq.html) and [updated FAQ](https://www.asd-ste100.org/STE_faq.html): controlled vocabulary and clear sentence structure | Short sentences, clear actors, consistent software terms, and fidelity exceptions | A selective user preference, not formal compliance. Direct page fetches returned 403; official indexed text was available. No full dictionary audit occurred. |
| [Google: What to look for in a code review](https://google.github.io/eng-practices/review/reviewer/looking-for.html): design, behavior, complexity, tests, and concurrency deserve assessment | Concrete findings, behavior-based checks, and explicit design tradeoffs | Scale review effort to assignment risk. Do not require a large ceremony for every edit. |
| [pstack](https://github.com/cursor/plugins/tree/main/pstack): task-specific engineering playbooks | Load short relevant guides rather than a whole library | Do not import model defaults, automatic shipping, or unrelated workflows. GitHub's tree view failed to load; raw source files were read. |

Specific pstack sources informed these adaptations:

- [Model the domain](https://github.com/cursor/plugins/blob/main/pstack/skills/principle-model-the-domain/SKILL.md): represent real invariants without speculative abstraction.
- [Subtract before you add](https://github.com/cursor/plugins/blob/main/pstack/skills/principle-subtract-before-you-add/SKILL.md): simplify demonstrated complexity.
- [Boundary discipline](https://github.com/cursor/plugins/blob/main/pstack/skills/principle-boundary-discipline/SKILL.md): concentrate external validation at boundaries.
- [Prove it works](https://github.com/cursor/plugins/blob/main/pstack/skills/principle-prove-it-works/SKILL.md): inspect real results.
- [Test behavior](https://github.com/cursor/plugins/blob/main/pstack/skills/principle-test-behavior-not-implementation/SKILL.md): check observable contracts.

TaskAllot resolves tensions explicitly. Simplification preserves required validation and caller behavior. Internal types do not justify ignoring mutable-state or replay risks. Evidence requirements scale with the task; unavailable checks remain visible.

The [engineering guide](../plugin/guidance/engineering.md) owns the compact common rules. The [writing profile](../plugin/guidance/writing.md) owns presentation rules.

## Attribution and later reuse

This scaffold summarizes and adapts principles. It does not copy a third-party guidance library.

[pstack's license](https://github.com/cursor/plugins/blob/main/pstack/LICENSE) is MIT, copyright 2026 Lauren Tan. Later substantial reuse must retain its copyright and permission notice.

[Google's repository license](https://github.com/google/eng-practices/blob/master/LICENSE) is CC BY 3.0. Later reuse must preserve required attribution and notices, link the license, and identify adaptations.

These license files were inspected. Before verbatim reuse, verify the exact source revision, file-specific notices, and applicable requirements. ASD text and marks are not treated as freely reusable library content.
