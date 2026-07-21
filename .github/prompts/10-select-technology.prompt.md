---
name: 10 Select Technology
description: "Evaluate and select frontend, backend, data, integration, and operational technologies against approved architecture drivers and team constraints."
argument-hint: "Optional preferred or prohibited technologies and team skills"
agent: Solution Architect
tools: [read, search, web, edit, vscode/askQuestions]
---

Select a maintainable technology stack for the approved architecture.

- Use `docs/templates/technology-selection.md` and save `docs/architecture/technology-selection.md`.
- Compare options against requirement fit, maintainability, security, compliance, operations, total cost, ecosystem, support lifecycle, license, and team capability.
- Record evidence and uncertainty; add proof activities for material unknowns.
- Define supported runtime and package-manager versions plus expected build, test, lint, and run commands.
- Update ADRs, risks, decisions, and traceability where the selection changes consequences.

Do not scaffold or install the selected stack in this step.
