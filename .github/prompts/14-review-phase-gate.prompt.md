---
name: 14 Review Phase Gate
description: "Run an independent read-only quality review of the current or specified phase and return findings plus a PASS, CONDITIONAL, or FAIL verdict."
argument-hint: "Phase name or implementation TASK-NNN"
agent: Quality Reviewer
tools: [read, search, execute, vscode/askQuestions]
---

Review the requested phase or implementation task against `docs/project-status.md`, required templates, approved upstream artifacts, and traceability.

When the mode is `短時間試作`, review the primary flow using the selected `確認方法`. With `最後にまとめて確認`, run one consolidated review. With `工程ごとに確認`, include the recorded approvals and changes from each process in the final review. Require executed validation and linked `REQ`, `TASK`, and `TEST` evidence. Treat recorded optional-document omissions as limitations, not automatic failures. Return `FAIL` when the primary flow is not runnable, validation is absent or failing, evidence is contradictory, or a critical safety condition remains.

- Check required sections, evidence quality, assumptions, contradictions, unresolved risks, and stable-ID links.
- Check that the current operation's start and end datetimes were captured through `execute`, include UTC offsets, and produce a consistent elapsed duration. Report `時刻未記録` for the current operation as a procedure failure, while leaving unrecoverable historical records unchanged.
- For implementation, require acceptance evidence and actual validation results.
- List findings first in severity order with artifact paths and IDs.
- Summarize requirement and test coverage.
- Return exactly one verdict: `PASS`, `CONDITIONAL`, or `FAIL`, with required actions.

Do not edit files, implement corrections, or grant user approval.
