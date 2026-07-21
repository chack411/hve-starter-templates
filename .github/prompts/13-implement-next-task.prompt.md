---
name: 13 Implement Next Task
description: "Implement and validate one approved dependency-ready TASK vertical slice, including source, tests, task evidence, and traceability updates."
argument-hint: "TASK-NNN, or leave blank to select the first ready approved task"
agent: Implementation Engineer
tools: [read, search, edit, execute, vscode/askQuestions]
---

Implement exactly one approved implementation task. In `短時間試作`, the kickoff-confirmed primary flow provides prototype approval for its task.

1. Select the requested task or the first approved dependency-ready task. In `短時間試作`, select the primary-flow task marked ready for prototype implementation.
2. Verify its `REQ`, acceptance criteria, tests, validation command, and any material `ADR`; stop if required information is missing.
3. Inspect the nearest controlling code and existing test pattern.
4. Make the smallest task-scoped change and immediately run the narrowest relevant executable check.
5. Add or update tests and rerun focused validation.
6. Create or update `src/README.md` after implementation so it accurately describes the application's purpose and scope, source structure, implemented architecture and data flow, prerequisites, safe configuration, setup, run, build, lint, test, primary-use, and troubleshooting steps. Include only verified commands, identify unimplemented plans explicitly, and write `該当なし` with a reason for commands the application does not provide.
7. Check README paths against the source tree and commands against package scripts or build configuration, run every documented command that applies, then update the task's completion evidence and the traceability matrix.

Do not expand scope, implement a second task, record unrun tests as passing, or mark user approval.
