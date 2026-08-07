---
name: artifact-workflow
description: "Manage the research-to-implementation artifact workflow. Use when starting, continuing, gating, reopening, or handing off phases through project brief, research, requirements, architecture, delivery, implementation, and review."
argument-hint: "Current phase or desired workflow action"
---

# Artifact Workflow

## Source of State

Read `docs/project-status.md` first. It is the only phase-status and approval ledger. Artifacts describe work; they do not grant their own approval.

Use plain Japanese in user-facing status and guidance. Prefer 工程, 作るもの, 完了の目安, 確認待ち, and 入力待ち（HIL） over phase, artifact, exit criteria, gate, and blocked.

## Phase Order

1. Initiation: project brief and research questions
2. Research: market, alternatives, patterns, and source register
3. Analysis: current state and KPI catalog
4. Product definition: testable requirements and MVP boundary
5. Architecture: data, system, API, and technology decisions
6. Delivery planning: milestones, test strategy, and tasks
7. Implementation: one approved task at a time
8. Quality review: independent coverage and evidence verdict

## Workflow Modes

Use `通常` unless `docs/project-status.md` says `短時間試作`.

### 短時間試作

Use this mode for a prototype or small MVP whose purpose is learning, demonstration, or usability checks. At the start, confirm the outcome, one primary user flow, time limit, excluded scope, and `確認方法`. Record `確認方法` as either `工程ごとに確認` or `最後にまとめて確認`.

Aim to finish the full flow within the confirmed time limit:

| Order | Work | Minimum result |
| --- | --- | --- |
| 1 | Start | Problem, user, primary flow, exclusions, and success check |
| 2 | Focused research and current state | Only decision-changing facts, sources, and assumptions |
| 3 | MVP and design | Testable requirements and the simplest reversible design |
| 4 | Implementation preparation | One vertical-slice task and focused test plan |
| 5 | Implementation | Working primary flow with automated checks |
| 6 | Final review | Executed validation, known limitations, and next decision |

For each intermediate process, run a lightweight self-check and record assumptions and skipped work. With `最後にまとめて確認`, set the process to `仮完了` and continue immediately without human confirmation. Run one consolidated independent review at the end. With `工程ごとに確認`, set the process to `入力待ち（HIL）`, show the outputs, check result, omissions, and risks, and ask the user to approve or request changes. Mark an approved process row `完了`, clear HIL, and set the overall status to the next process's `作業中`; return a process with requested changes to `作業中` and ask again after repair. Regardless of confirmation method, set the final review to `確認待ち`.

Keep only the documents needed to make and verify the prototype. Sections may be compact, and non-applicable documents may be skipped when the reason is recorded in `docs/project-status.md`. Keep stable IDs only for the primary flow: at least one `REQ`, `TASK`, and `TEST`, plus an `ADR` when a material design choice exists.

Do not use automatic continuation for production release, real confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or an irreversible architecture choice. Set `入力待ち（HIL）` and ask before those actions regardless of `確認方法`. If the confirmed time limit becomes unrealistic, preserve a runnable primary flow, move optional work to known limitations, and continue according to the selected confirmation method.

## Record Execution Time

For every project-output creation, update, or review. Do not write session-specific execution rows into repository templates, README files, instructions, skills, prompts, or the uninitialized `docs/project-status.md` template.

1. Capture the system clock at the start. Add a new row to the document's `実行記録` and to `docs/project-status.md` with the start datetime.
2. Use `YYYY-MM-DD HH:mm:ss ±HH:mm`, including the local UTC offset. Do not reuse the conversation date as an execution time.
3. At the end, capture the system clock again. Fill the same row's end datetime and elapsed duration.
4. Append records. Never replace earlier execution rows.
5. For a phase, also update the matching `工程一覧` row. Record the phase start when it becomes `作業中`, and its end and duration when it becomes `仮完了`, `確認待ち`, or `完了`.
6. Leave a running process without an end datetime. Do not count time waiting for human input unless the recorded duration explicitly says it includes waiting time.

## Start a Phase

1. In `通常`, confirm the preceding gate is approved. In `短時間試作`, accept `仮完了` with `最後にまとめて確認` or explicit approval recorded as `完了` with `工程ごとに確認`.
2. Read approved upstream artifacts and traceability.
3. Identify required outputs, owners, open questions, and risks.
4. Capture and record the phase start datetime.
5. Set the current process to `作業中` and name the document being created.

In `docs/project-status.md`, write these values as `作業中`, `現在の工程`, `現在の工程の開始日時`, and `作成中の文書`.

## Complete a Phase

In `通常`:

1. Run each required template checklist.
2. Check links, stable IDs, evidence, assumptions, and unresolved risks.
3. Request an independent quality review.
4. Capture the phase end datetime, calculate the elapsed duration, and record both before setting status to `確認待ち`.
5. Set status to `確認待ち`; never invent user confirmation.
6. After explicit approval, record approver and confirmation datetime, update the decision log, then activate the next phase.

In the user-facing progress table, use `確認待ち` before approval and `完了` after approval.

In `短時間試作`:

1. Check only what is needed to support the primary flow and the next decision.
2. Record missing evidence, assumptions, skipped documents, and risks.
3. With `最後にまとめて確認`, set the intermediate process to `仮完了` and continue without stopping. Reserve `確認待ち` for the consolidated final review or a safety-related decision.
4. Capture and record the phase end datetime and elapsed duration before setting it to `仮完了`, `入力待ち（HIL）`, or `確認待ち`.
5. With `工程ごとに確認`, set an intermediate process to `入力待ち（HIL）`, fill every HIL field, and ask for `承認` or `修正`. After `承認`, record the approver and confirmation datetime, mark that process row `完了`, clear the HIL section, set the overall status to the next process's `作業中`, and start it. After `修正`, capture a new start datetime, set the process to `作業中`, clear the HIL section, apply the requested changes, rerun the lightweight check, and ask again. This rule does not replace the final review's `確認待ち` state.

## Wait for Human Input (HIL)

1. Confirm the answer is truly blocking and cannot be found in existing documents or research.
2. Set the current status to `入力待ち（HIL）` before asking.
3. Fill in what must be decided, why it is needed, answer format, recommendation, what starts after the answer, owner, and a resume prompt.
4. List 2-4 choices with their consequences when the decision is selectable.
5. Ask through VS Code `askQuestions` using the same wording.
6. After the answer, record it in the owning document, clear the HIL entry, return to `作業中`, and continue.

Never leave the user with only `Blocked`, `Waiting`, or `Need input`. Always show a concrete answer example and the next work it unlocks.

## Show the Next Action

Whenever status changes, update `次にすること` with action, start condition, owner, prompt candidate, and completion guide. Recommend one prompt and list no more than two alternatives.

## Reopen a Gate

When new evidence invalidates confirmed work, record the triggering evidence, affected IDs, impact assessment, and decision in the log. Set the earliest affected process to `作業中`; later documents remain visible but are no longer authoritative until reviewed.

## Handoff Contract

A handoff states current phase, approved inputs, exact output path, completion criteria, stable IDs affected, constraints, open questions, and prohibited scope. Do not assign concurrent edits to the same artifact.
