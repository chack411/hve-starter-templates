---
name: 07 Design Data Model
description: "Design the conceptual and logical data model, dictionary, quality rules, history, audit, retention, import, indexing, partitioning, and recovery approach."
argument-hint: "Optional source schemas, volume estimates, retention, or compliance constraints"
agent: Solution Architect
---

Design data behavior for approved MVP requirements.

- Confirm the Product definition process is ready as `artifact-workflow` > `Start a Phase` defines; otherwise report the blocker and stop. In `短時間試作`, design only data needed by the primary flow.
- Use `docs/templates/data-design.md` and save `docs/architecture/data-design.md`.
- Include a Mermaid ER diagram, entity and attribute definitions, source mappings, validation, ownership, classification, history, audit, deletion, retention, backup, and recovery.
- Justify normalization, indexes, partitioning, and import reconciliation using access and volume assumptions.
- Link every material rule to requirements and update traceability and risks.

Do not generate database migrations or application code.
