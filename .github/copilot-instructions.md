# Project Guidelines

These rules apply to every chat in this repository. Detailed procedures live in one place each; this file states the rule, why it exists, and where the procedure is.

| Procedure | Owner |
| --- | --- |
| Workflow modes, phase states, HIL, execution-time recording | `.github/skills/artifact-workflow/SKILL.md` |
| Project kickoff | `.github/skills/hve-kickoff/SKILL.md` |
| `src/README.md` content | `.github/instructions/source-code.instructions.md` |
| Review verdicts | `.github/skills/deliverable-quality-gate/SKILL.md` |

## Workflow

- Read `docs/project-status.md` before creating or changing project artifacts. It is the only ledger for phase status and approval.
- Reuse approved upstream artifacts. Do not silently replace approved decisions.
- Use `通常` unless `docs/project-status.md` selects `短時間試作`. In `短時間試作`, the kickoff records `確認方法` as `工程ごとに確認` or `最後にまとめて確認`, and `artifact-workflow` defines what each one does.
- In `通常`, a process is complete only after its completion guide is met and a person's confirmation is recorded.
- Always stop for a person before production release, real confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or irreversible decisions. These can cause harm that a later review cannot undo, so no mode or confirmation method skips this stop.
- Record missing information as an open question or explicit assumption instead of inventing facts.
- When a person's input blocks progress, fill in the `入力待ち（HIL）` section of `docs/project-status.md` before asking with VS Code `askQuestions`, so the user can answer later from the file alone.

## Agent Tools

- Each custom agent's `tools` field is the single source of truth for that role's capabilities. Keep it at least privilege.
- Omit `tools` from prompt files so they inherit the agent's tools; a prompt-level `tools` field replaces the agent list rather than extending it.
- `execute` is the tool set that exposes terminal execution. When a procedure needs `execute`, call the available terminal tool.

## Evidence

- Separate verified facts, inferences, assumptions, and recommendations.
- Prefer primary and current sources. For material external claims, record the URL, publication or update date when available, access date, and confidence.
- Never fabricate citations, metrics, customer examples, benchmarks, test results, or approvals. Readers act on these records as if they were checked.

## Traceability

- Use stable IDs: `INSIGHT-NNN`, `KPI-NNN`, `REQ-NNN`, `ADR-NNN`, `TASK-NNN`, and `TEST-NNN`.
- Link requirements to insights or KPIs, decisions to requirements, tasks to requirements, and tests to tasks and requirements.
- Update `docs/project/traceability-matrix.md` when adding or changing a tracked item.

## Implementation

- Change `src/` and `tests/` only for an approved implementation task. In `短時間試作`, a task inside the kickoff-confirmed primary flow is approved when it has linked `REQ`, `TASK`, and `TEST` IDs and an explicit validation command.
- Follow the selected architecture and existing patterns. Keep changes within the task and add no credentials or production data.
- Add or update tests for every behavioral change, run the task's validation, and record the actual commands, results, and remaining risks in the task.

## Documentation

- In `通常`, start from `docs/templates/` and keep required sections. In `短時間試作`, keep only documents needed to build and verify the primary flow, and record skipped documents in `docs/project-status.md`.
- Record the start datetime, end datetime, and elapsed time of every project-output creation, update, or review from actual clock calls before the first edit and after validation. On Windows, run `$now = [DateTimeOffset]::Now; [pscustomobject]@{ datetime = $now.ToString('yyyy-MM-dd HH:mm:ss zzz'); epochMilliseconds = $now.ToUnixTimeMilliseconds() } | ConvertTo-Json -Compress`; always make the call, because whether it works is known only from its result. The fallback and failure handling are in `artifact-workflow` > `Record Execution Time`. Time is measured, not estimated, because the records are used to compare effort and to pace `短時間試作`.
- Keep templates, README files, instructions, skills, prompts, and the uninitialized `docs/project-status.md` free of session-specific records.
- Match document length to what the reader needs. Do not pad with filler sections, repeated summaries, or boilerplate.
- Write user-facing text in plain Japanese with short sentences. Prefer `工程`, `作るもの`, `完了の目安`, `確認待ち`, and `入力待ち（HIL）`, and explain unavoidable abbreviations at first use.
- Use Mermaid for diagrams and relative links. Update affected indexes and decision records.
- End user-facing progress reports with the recommended next action, required input, what starts next, and one to three prompt candidates.
