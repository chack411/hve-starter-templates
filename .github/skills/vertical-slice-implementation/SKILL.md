---
name: vertical-slice-implementation
description: "Implement one approved vertical-slice TASK from requirements and architecture through source, tests, focused validation, evidence, and traceability. Use when coding an approved TASK-NNN."
argument-hint: "TASK-NNN"
---

# Vertical-Slice Implementation

## Readiness Gate

Before editing, confirm that the task:

- is approved and dependency-ready; in `短時間試作`, the kickoff-confirmed primary flow provides prototype approval, so no separate task approval is needed inside that scope
- links requirements and any material architecture decisions
- defines observable acceptance criteria and excluded scope
- names planned test IDs and a focused validation command
- has no blocking open question

When an item is absent, stop and report the planning gap.

## Working Approach

Read the task with its linked `REQ`, `ADR`, risk, and test-strategy sections, then the nearest code that owns the behavior and its adjacent tests. Build the slice in small increments and run the focused validation after each one, so a failure points to the change that caused it. Fix failures inside the slice before widening scope. Add the normal, error, boundary, authorization, concurrency, or recovery tests that the acceptance criteria call for.

## Done When

1. All acceptance criteria pass through the task's validation command, run in this session.
2. `src/README.md` matches the implemented application as `.github/instructions/source-code.instructions.md` specifies, and each command it documents was run.
3. The task artifact records changed paths, commands with their actual results, unrun checks labeled as unrun, and remaining risks.
4. `docs/project/traceability-matrix.md` links the task to its `REQ` and `TEST` IDs.

## Scope Control

- One task per invocation.
- Preserve existing patterns and public contracts unless the task changes them.
- Leave unrelated refactors and dependency upgrades out.
- Keep tests and quality gates at the strength the task requires.
- Add no secrets, credentials, or copied production data.

## Completion Report

Return task and requirement IDs, behavior delivered, changed paths, tests added or updated, commands and results, documentation updates, remaining risks, and follow-up task IDs.
