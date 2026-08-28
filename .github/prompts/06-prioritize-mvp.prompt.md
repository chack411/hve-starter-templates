---
name: 06 Prioritize MVP
description: "Create testable product requirements and prioritize the smallest coherent MVP by value, learning, effort, operations, and readiness."
argument-hint: "Optional candidate capabilities, constraints, or release target"
agent: Product Planner
tools: [read, search, edit, execute, vscode/askQuestions]
---

Define and prioritize the product outcome from approved research, current-state analysis, and KPI catalog.

1. Create `docs/requirements/product-requirements.md` from its template.
2. Create `docs/requirements/mvp-prioritization.md` from its template.
3. Assign stable `REQ-NNN` IDs and measurable acceptance criteria.
4. Score candidates with agreed criteria and document evidence for each score.
5. Define MVP inclusions, later work, explicit exclusions, and assumptions to validate.
6. Update the decision log and traceability matrix.

Do not choose implementation technology. In `通常`, stop at `確認待ち`; human confirmation is required before architecture. In `短時間試作`, keep no more than three requirements for one primary flow and record exclusions and assumptions. With `最後にまとめて確認`, set this process to `仮完了` and continue to architecture. With `工程ごとに確認`, set it to `入力待ち（HIL）` and continue only after explicit approval marks it `完了`.
