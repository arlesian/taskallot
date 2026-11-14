# Plugin and controller boundary

This outline identifies future package responsibilities. Inputs are the skill workflow, job profiles, guidance, and controller design. Output is a packaging discussion, not a manifest.

Use the [shared vocabulary](../controller/task-assessment.md). [Integration](../controller/codex-integration.md) owns invocation evidence and host compatibility.

| Component | Responsibility | Boundary |
| --- | --- | --- |
| Plugin | Expose five user-facing skills, job profiles, and relevant coding guidance | Guidance does not enforce runtime authority. |
| Small local controller | Maintain state, lifecycle, messages, accounting, dispatch, and monitoring data | Implementation language and storage engine remain open. |
| Manager agent | Make coordination decisions and allocate authorized work | Uses controller state; source implementation belongs to developers. |
| Terminal monitor | Render stored status and budget observations | Routine refresh invokes no model. |

The plugin can recommend or prepare configuration before any run exists. Setup later starts selected work under its authorization envelope. Agents and status inspect the resulting records.

The local controller provides runtime mechanisms that prose alone cannot guarantee. Its host connection, startup model, durable writes, and restart behavior require a future prototype.

Package metadata, supported installation layout, distribution, and exact skill registration remain unresolved. Proposed runtime paths belong to [communication](../controller/agent-communication.md), not package structure.

For example, removing an auditor through plan editing changes assignments and estimates. It does not stop or duplicate an already active assignment automatically.
