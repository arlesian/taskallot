# Plugin boundary and packaging outline

This document identifies what a future plugin would need to expose. It uses the [proposal interaction](skills/propose/SKILL.md), the four role descriptions, and the controller documents. Its result is a packaging discussion, not a manifest or an installation contract.

The proposed package would carry a discoverable description of the proposal capability, its skill guidance, role references, and references for assessment, estimation, selection, and scheduling. The controller is a design responsibility; whether it becomes skill guidance, host functionality, or a separate service is unresolved.

The plugin's output is a reviewable proposal. Worker execution and any authorization mechanism belong to a later integration design. For example, a user could change a proposed two-worker assignment to one worker and request a refreshed estimate before execution is considered.

The exact meaning of `/propose` in Codex, any metadata fields, file placement required by a package loader, and distribution format remain unverified. [Codex integration](../controller/codex-integration.md) owns those capability questions; [open decisions](../OPEN-QUESTIONS.md) records the proposed defaults.
