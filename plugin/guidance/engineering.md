# Common engineering guidance

Use this short guide for source-changing assignments. Load [debugging](debugging.md), [experiments](experiments.md), [concurrency](concurrency.md), or [review](review.md) only when relevant.

Inputs are the assignment, acceptance criteria, repository instructions, and existing code. Output is a focused change with evidence and explicit gaps. Repository-specific instructions take precedence over these defaults.

- Read relevant code and repository instructions before editing.
- Reuse existing logic and conventions when they fit the required behavior.
- Prefer a function for a straightforward transformation.
- Add a class when state, lifecycle, or invariants justify it.
- Avoid speculative factories, interfaces, wrappers, and layers.
- Keep mutable state narrow.
- Make ownership explicit.
- Preserve required caller behavior while addressing demonstrated causes.
- Validate external inputs at boundaries.
- Report errors accurately.
- Test observable behavior against requirements through the real entry point.
- Keep changes focused.
- Provide concise evidence and unresolved gaps in the handoff.

Simplification must preserve required validation and supported behavior. Internal types do not remove risks from mutable state, stale observations, or external effects. Add protection where evidence or requirements justify it.

These are TaskAllot adaptations of [pstack and Google's guidance](../../docs/design-sources.md#writing-and-engineering). They do not import either library wholesale. Use the [writing profile](writing.md) for explanations.
