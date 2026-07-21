---
name: vertical-slice-implementation
description: "Implement one approved vertical-slice TASK from requirements and architecture through source, tests, focused validation, evidence, and traceability. Use when coding an approved TASK-NNN."
argument-hint: "TASK-NNN"
---

# Vertical-Slice Implementation

## Readiness Gate

Before editing, verify that the task:

- is approved and dependency-ready; in `短時間試作`, the kickoff-confirmed primary flow provides prototype approval
- links requirements and any material architecture decisions
- defines observable acceptance criteria and excluded scope
- names planned test IDs and a focused validation procedure
- has no blocking open question

Stop and report a planning gap when any item is absent. Do not require a separate task approval in `短時間試作` when the task remains within the kickoff-confirmed scope.

## Procedure

1. Read the task and every linked `REQ`, `ADR`, risk, and test-strategy section.
2. Search from the most concrete code anchor to the nearest behavior-owning implementation and adjacent test.
3. State one falsifiable local hypothesis and one inexpensive check that could disconfirm it.
4. Make the smallest grounded edit for one acceptance behavior.
5. Immediately run the narrowest executable test, type check, build, or lint action for that behavior.
6. If it fails within the same slice, repair locally and rerun before widening scope.
7. Add normal, error, boundary, authorization, concurrency, or recovery coverage required by the acceptance criteria.
8. Run all task-required validation and record commands and actual results.
9. Create or update `src/README.md` to match the implemented application. Include purpose and scope, source structure, implemented architecture and data flow, prerequisites, safe configuration, setup, run, build, lint, test, primary-use, and troubleshooting instructions. Record only verified commands, identify unimplemented plans explicitly, and write `該当なし` with a reason for commands the application does not provide.
10. Check README paths against the source tree and commands against package scripts or build configuration, run every documented command that applies, then update the task evidence and traceability matrix. Record unrun checks and residual risk; do not call them passing.

## Scope Control

- One task per invocation.
- Preserve existing patterns and public contracts unless the task changes them.
- Avoid unrelated refactors and dependency upgrades.
- Never weaken a test or quality gate to obtain a pass.
- Never add secrets, credentials, or copied production data.
- Do not complete the first runnable application task while `src/README.md` still contains placeholder instructions.

## Completion Report

Return task and requirement IDs, behavior delivered, changed paths, tests added or updated, commands and results, documentation updates, residual risks, and follow-up task IDs.
