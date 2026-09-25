---
name: 14 Review Phase Gate
description: "Run an independent read-only quality review of the current or specified phase and return findings plus a PASS, CONDITIONAL, or FAIL verdict."
argument-hint: "Phase name or implementation TASK-NNN"
agent: Quality Reviewer
---

Review the requested phase or implementation task against `docs/project-status.md`, required templates, approved upstream artifacts, and traceability, following the `deliverable-quality-gate` skill. When the mode is `短時間試作`, apply its `短時間試作 Review` section for the selected `確認方法`.

- List every finding first, in severity order, with artifact paths and IDs.
- Summarize requirement and test coverage.
- Return exactly one verdict: `PASS`, `CONDITIONAL`, or `FAIL`, with required actions.

This review is read-only: report corrections rather than making them, and leave approval to the user.
