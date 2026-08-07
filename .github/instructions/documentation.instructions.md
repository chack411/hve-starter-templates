---
name: Documentation
description: "Use when creating or updating project documentation, templates, registers, plans, decisions, or review reports."
applyTo: "docs/**"
---

# Documentation Rules

- In `通常`, start from the matching file in `docs/templates/` and keep required sections and completion checklists.
- In `短時間試作`, keep only documents and sections needed to decide, build, and verify the primary flow. Record every skipped document or section, its reason, and its effect in `docs/project-status.md`.
- Keep project outputs outside `docs/templates/`.
- Write for a reader who is new to the project. Use plain Japanese, short sentences, direct verbs, and one idea per sentence.
- Replace or explain specialist terms. Prefer `作るもの` for artifact, `工程` for phase, `完了の目安` for exit criteria, `確認ポイント` for gate, and `つながり` for traceability in user-facing text.
- Keep standard identifiers and common technical names such as `REQ-NNN`, KPI, API, and ADR, but explain them at first use.
- Use relative links, stable IDs, ISO dates (`YYYY-MM-DD`), and consistent project terminology. Use `YYYY-MM-DD HH:mm:ss ±HH:mm` for execution, update, decision, and confirmation datetimes.
- For every project-output creation, update, or review, append an `実行記録` row with the actual start datetime, end datetime, elapsed duration, and actor. Do not overwrite prior rows or infer missing historical times.
- Do not add session-specific execution records to repository templates, README files, or the uninitialized `docs/project-status.md` template. Keep only placeholders and examples there.
- Mark status, owner, inputs, assumptions, open questions, and approval explicitly.
- When status is `入力待ち（HIL）`, state what to answer, answer examples or choices, recommendation, what starts after the answer, owner, and a copy-ready resume prompt.
- Show a `次にすること` section with one recommended prompt and no more than two alternatives.
- Use Mermaid rather than binary diagrams when practical.
- Do not claim approval, completion, evidence, test execution, or source verification that did not occur.
- Update affected indexes, registers, project status, and traceability links.
