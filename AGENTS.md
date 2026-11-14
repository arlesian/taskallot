# Instructions for contributors

Keep this repository a prose design scaffold until the user explicitly requests implementation. Use Markdown and plain English. Do not add executable code, pseudocode, manifests, package files, installation scripts, dependencies, or automated tests during this phase.

Give each design decision one home and link to it with relative links. Keep each file focused enough that a reviewer can change one decision without rewriting the repository. Describe purpose, inputs, and result; include a concrete example when it clarifies a tradeoff.

Use the vocabulary defined in [task assessment](controller/task-assessment.md). Keep examples aligned with the canonical format in [SKILL.md](plugin/skills/propose/SKILL.md). Label all invented quantities as illustrative. Do not turn estimates into measurements or unknown integration capabilities into guarantees.

Record consequential unresolved choices and proposed defaults in [OPEN-QUESTIONS.md](OPEN-QUESTIONS.md), linking to their owning files. Before submitting a prose change, read the affected descriptions and examples together, inspect relative links, and check that no implementation artifacts have entered the repository.
