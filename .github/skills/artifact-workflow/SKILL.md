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

Use `通常` unless `docs/project-status.md` says `短時間試作`. The kickoff procedure for both modes is in the `hve-kickoff` skill.

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

This section is the single definition of `短時間試作`. Agents, prompts, and other skills refer to it instead of restating it.

For each intermediate process, run a lightweight self-check and record assumptions and skipped work. With `最後にまとめて確認`, set the process to `仮完了` and continue immediately without human confirmation. Run one consolidated independent review at the end. With `工程ごとに確認`, set the process to `入力待ち（HIL）`, show the outputs, check result, omissions, and risks, and ask the user to approve or request changes. Mark an approved process row `完了`, clear HIL, and set the overall status to the next process's `作業中`; return a process with requested changes to `作業中` and ask again after repair. Regardless of confirmation method, set the final review to `確認待ち`.

Keep only the documents needed to make and verify the prototype. Sections may be compact, and non-applicable documents may be skipped when the reason is recorded in `docs/project-status.md`. Keep stable IDs only for the primary flow: at least one `REQ`, `TASK`, and `TEST`, plus an `ADR` when a material design choice exists.

Scope limits: at most two research questions that can change the prototype decision, one primary flow, and no more than three `REQ` IDs. Choose the simplest reversible design and add no optional infrastructure, integrations, or abstractions.

Delegation: hand off only focused research (`Market Researcher`, one request covering all questions), implementation (`Implementation Engineer`), and the final review (`Quality Reviewer`). The HVE Lead writes the compact current-state, requirement, design, and implementation-preparation documents itself, because a separate agent for each short document costs more time than it saves.

Time budget: each time the clock command runs, compute the elapsed time since the kickoff start and write `経過 X分 / 制限 Y分` in the `経過時間` row of the `現在の状況` table in `docs/project-status.md`. Use it to pace the work: a correct result reached earlier is better, and when time runs short, drop optional scope rather than the primary-flow tests.

With `最後にまとめて確認`, an incomplete optional document is not a reason to stop: record the gap, protect the runnable primary flow, and carry the gap to the final review. With `工程ごとに確認`, include the gap in that process's HIL confirmation and follow the user's decision.

Always set `入力待ち（HIL）` and ask before production release, real confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or an irreversible architecture choice, whatever the `確認方法`. If the confirmed time limit becomes unrealistic, preserve a runnable primary flow, move optional work to known limitations, and continue according to the selected confirmation method.

## Record Execution Time

This section is the single definition of execution-time recording. Apply it to every project-output creation, update, or review. The records are used to compare effort across projects and to pace `短時間試作`, so every value must come from an actual clock call. Keep session-specific rows out of repository templates, README files, instructions, skills, prompts, and the uninitialized `docs/project-status.md` template.

1. `execute` is the frontmatter tool set that exposes a terminal-execution tool. Call whichever terminal tool the runtime provides; its display name may differ. Whether the command can run is known only from an actual call result, so always make the call before concluding anything about it.
2. Before the first edit or review action, invoke the terminal tool. On Windows, run this exact PowerShell command:

	```powershell
	$now = [DateTimeOffset]::Now; [pscustomobject]@{ datetime = $now.ToString('yyyy-MM-dd HH:mm:ss zzz'); epochMilliseconds = $now.ToUnixTimeMilliseconds() } | ConvertTo-Json -Compress
	```

	On Linux or macOS, run a platform-equivalent command that returns both local datetime with UTC offset and Unix epoch milliseconds. The conversation date, file timestamps, and estimates are not acceptable substitutes.
3. Accept the result when the call succeeded, `datetime` matches `YYYY-MM-DD HH:mm:ss ±HH:mm`, and `epochMilliseconds` is numeric. Append the start row to the output document and `docs/project-status.md`, and keep the epoch value for the elapsed-time calculation.
4. If the Windows command returns an error, retry once with `Get-Date -Format "yyyy-MM-dd HH:mm:ss zzz"`.
5. After the substantive work and its validation, but before the final status or execution-record edit, invoke the same clock command again. Record its `datetime` as the end datetime and calculate elapsed duration from the captured epoch values. If the fallback command was required, parse the two returned datetimes with their offsets and subtract them.
6. Append records. Never replace earlier execution rows. For a phase, also update the matching `工程一覧` row. Record the phase start when it becomes `作業中`, and its end and duration when it becomes `仮完了`, `入力待ち（HIL）`, `確認待ち`, or `完了`.
7. Leave a running process without an end datetime. Before entering HIL, capture the current end time; after resumption, capture a new start time. Do not count waiting time unless the record explicitly says it includes waiting time.
8. Use `時刻未記録` for the current operation only when the runtime has no terminal tool, or when the primary call and its fallback both actually returned errors. Uncertainty about command support is not a reason; make the calls. Record the attempted commands and errors, set duration to `未記録`, and report that time recording failed. Keep `時刻未記録` for historical entries whose actual time cannot be recovered.
9. Specialists record their own times with their own calls; a parent-captured time does not substitute. They return the captured values, elapsed duration, and any command errors in their result.

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

A handoff states current phase, approved inputs, exact output path, completion criteria, stable IDs affected, constraints, open questions, and prohibited scope. For any creation, update, or review of a project output, require the specialist to capture and return the actual start datetime, end datetime, and elapsed duration according to `Record Execution Time`. Do not assign concurrent edits to the same artifact.
