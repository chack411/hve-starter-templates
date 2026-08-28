---
name: 08 Evaluate Architecture
description: "Compare viable architecture patterns against requirements and quality drivers, then record a recommended architecture and explicit trade-offs as ADRs."
argument-hint: "Optional deployment, integration, security, cost, or team constraints"
agent: Solution Architect
tools: [read, search, web, edit, execute, vscode/askQuestions]
---

Evaluate architecture options for the approved MVP.

- In `通常`, verify the Product definition process is approved. In `短時間試作`, accept `仮完了` with `最後にまとめて確認` or `完了` with `工程ごとに確認`, compare only materially different choices, and choose the simplest reversible option that supports the primary flow.
- Derive measurable decision drivers from requirements and constraints.
- Compare at least two viable options for material choices. In `短時間試作`, omit comparison for choices that are already fixed by the repository or are inexpensive to reverse.
- Record the recommendation as `docs/architecture/ADR-001-solution-architecture.md` using the ADR template.
- Include Mermaid context and component/data-flow diagrams.
- Cover security, identity, operations, availability, recovery, scaling, cost, migration, and lock-in.
- Update decision, risk, and traceability records.

Do not implement the architecture or hide unresolved proof activities.
