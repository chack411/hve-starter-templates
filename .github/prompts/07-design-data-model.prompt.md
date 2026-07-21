---
name: 07 Design Data Model
description: "Design the conceptual and logical data model, dictionary, quality rules, history, audit, retention, import, indexing, partitioning, and recovery approach."
argument-hint: "Optional source schemas, volume estimates, retention, or compliance constraints"
agent: Solution Architect
tools: [read, search, edit, vscode/askQuestions]
---

Design data behavior for approved MVP requirements.

- In `通常`, verify the Product definition process is approved; otherwise report the blocker and stop. In `短時間試作`, accept `仮完了` with `最後にまとめて確認` or `完了` with `工程ごとに確認`, and design only data needed by the primary flow.
- Use `docs/templates/data-design.md` and save `docs/architecture/data-design.md`.
- Include a Mermaid ER diagram, entity and attribute definitions, source mappings, validation, ownership, classification, history, audit, deletion, retention, backup, and recovery.
- Justify normalization, indexes, partitioning, and import reconciliation using access and volume assumptions.
- Link every material rule to requirements and update traceability and risks.

Do not generate database migrations or application code.
