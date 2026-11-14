# Concurrency and ownership guidance

Use this guide for concurrent source work or behavior involving partial failure, retries, and replay. Inputs include effect boundaries, ownership, workspace scope, and acceptance criteria. Output is an explicit ownership and failure model with relevant checks.

Give each source-changing assignment a clear owner. Proposed default: concurrent writers use separate worktrees. Assign integration to a named developer. Shared read-only evidence can use a common artifact reference.

Separate worktrees prevent accidental file overlap; they do not prevent incompatible changes or duplicate external effects. Serialize integration when scopes overlap. Re-audit affected behavior after integration.

Consider interruption before and after each durable effect. Distinguish replay of one logical operation from a genuinely new operation. Define how duplicate requests, partial results, and concurrent updates are observed and recovered.

Keep mutable state ownership explicit. Choose coordination mechanisms for the demonstrated consistency requirement. Do not add concurrency merely to increase agent count.

For duplicate essay scoring, a retry-safe record may still leave an unprotected downstream effect. Include both boundaries in acceptance evidence.

[Communication](../../controller/agent-communication.md) owns message delivery. [Source notes](../../docs/design-sources.md#coordination-and-recovery) explain the isolation pattern. Repository instructions override generic defaults.
