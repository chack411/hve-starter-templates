# Project Guidelines

## Workflow

- Read `docs/project-status.md` before creating or changing project artifacts.
- Reuse approved upstream artifacts. Do not silently replace approved decisions.
- Use `通常` unless `docs/project-status.md` selects `短時間試作`.
- In `通常`, do not mark a process complete until its completion guide is satisfied and human confirmation is recorded.
- In `短時間試作`, record `確認方法` as either `工程ごとに確認` or `最後にまとめて確認` at kickoff. After each lightweight check, stop in `入力待ち（HIL）` for the former or mark the process `仮完了` and continue for the latter.
- Never auto-continue into production release, confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or irreversible decisions.
- Record missing information as an open question or explicit assumption instead of inventing facts.
- When human input blocks progress, set `docs/project-status.md` to `入力待ち（HIL）` before using VS Code `askQuestions`. Record what to answer, available choices, what starts after the answer, and a resume prompt.
- After the answer, record the decision, clear the input wait, and continue when possible.

## Agent Tools

- Treat each custom agent's `tools` field as the single source of truth for that role's capabilities.
- Omit `tools` from prompt files so they inherit the referenced custom agent's tools. A prompt-level `tools` field replaces rather than extends the agent list.
- Add prompt-level tools only when a task intentionally needs a narrower capability set. In that case, specify the complete replacement list and explain the restriction in the prompt body.
- Keep agent tools at least privilege and retain a tool only when the agent instructions describe its use.

## Evidence

- Separate verified facts, inferences, assumptions, and recommendations.
- Prefer primary and current sources for external research.
- For material external claims, record the source URL, publication or update date when available, access date, and confidence.
- Never fabricate citations, metrics, customer examples, benchmarks, or research results.

## Traceability

- Use stable IDs: `INSIGHT-NNN`, `KPI-NNN`, `REQ-NNN`, `ADR-NNN`, `TASK-NNN`, and `TEST-NNN`.
- Link requirements to their supporting insights or KPIs, design decisions to requirements, implementation tasks to requirements, and tests to tasks and requirements.
- Update `docs/project/traceability-matrix.md` when adding or changing a tracked item.

## Implementation

- Change `src/` and `tests/` only for an approved implementation task. In `短時間試作`, a task within the kickoff-confirmed primary flow is approved for prototype implementation when it has linked `REQ`, `TASK`, and `TEST` IDs and an explicit validation command.
- Follow the selected architecture and the repository's existing patterns.
- Keep changes narrowly scoped and do not add credentials or sensitive production data.
- Add or update tests for every behavioral change and run the narrowest relevant validation first.
- Record validation evidence and unresolved risks in the implementation task.

## Documentation

- In `通常`, use the templates under `docs/templates/` and preserve their required sections. In `短時間試作`, keep only documents needed to build and verify the primary flow; record skipped documents and reasons in project status.
- For project outputs created from templates, use the `execute` tool to capture the system clock immediately before work and record that actual start datetime in the document's `実行記録`. Capture it again immediately after work and record the actual end datetime and elapsed duration. Append a row instead of overwriting prior records.
- Do not add session-specific execution records to repository templates, README files, instructions, skills, prompts, or the uninitialized `docs/project-status.md` template. Keep only placeholders and examples in template files.
- Use `YYYY-MM-DD HH:mm:ss ±HH:mm` for execution, update, decision, and confirmation datetimes. Keep date-only values for calendar dates such as deadlines and publication dates. Never infer missing historical times; mark them as `時刻未記録` and the duration as `未記録`.
- Record each process's start datetime, end datetime, and duration in `docs/project-status.md`. Keep the current process start datetime and update history synchronized with the document records.
- Use Mermaid for diagrams that benefit from version-controlled text.
- Keep links relative and update affected indexes and decision records.
- Write user-facing documents in plain Japanese. Use short sentences and familiar words; explain unavoidable abbreviations the first time.
- Prefer `工程`, `作るもの`, `完了の目安`, `確認待ち`, and `入力待ち（HIL）` over unexplained English workflow terms.
- End user-facing progress reports with the recommended next action, required input, what starts next, and one to three prompt candidates.
