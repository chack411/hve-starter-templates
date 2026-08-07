---
name: 00 Start Project
description: "Start an HVE application project in either normal or short-prototype mode, from kickoff through the mode-appropriate next step."
argument-hint: "Problem, users, desired outcome, and optionally the mode, time limit, primary flow, success check, exclusions, and confirmation method"
agent: Hyper Velocity Engineering Lead
tools: [read, search, edit, agent, todo, vscode/askQuestions]
---

Initialize this repository for the application described by the user. This is the single entry point for both `通常` and `短時間試作`.

## Common kickoff

1. Read `README.md`, `docs/project-status.md`, `docs/templates/project-brief.md`, existing project documents, and relevant repository patterns.
2. Read an explicitly stated `通常` or `短時間試作` as the user's mode choice. If no mode is stated, do not infer or select one on the user's behalf; include the mode as the first HIL choice. Recommend `短時間試作` for a prototype or small MVP and `通常` when durable decisions, broad evidence, or separate approvals are more important than reaching a runnable result quickly.
3. After the mode is known, ask only for missing information needed to define the problem, users, desired outcome, scope, constraints, and success measures. For `通常`, also confirm initial research questions. For `短時間試作`, also confirm the time limit, one primary user flow, its observable success check, explicit exclusions, and whether `確認方法` is `工程ごとに確認` or `最後にまとめて確認`.
4. Before asking, set `docs/project-status.md` to `入力待ち（HIL）` and fill in what to answer, answer examples or choices, what starts after each choice, and a resume prompt. Use `askQuestions`.
5. After the answer, record `進め方` and any mode-specific values, clear the HIL entry, and continue in the same request. Do not require another kickoff prompt.
6. Record actual start and end datetimes and elapsed duration as required by the artifact workflow. If either timestamp was not captured, do not infer it; mark that timestamp as `時刻未記録` and the duration as `未記録`.

## Normal mode

When `進め方` is `通常`:

1. Create `docs/project/project-brief.md`, `source-register.md`, `decision-log.md`, `risk-register.md`, and `traceability-matrix.md` from their templates.
2. Set the 開始準備 row in `docs/project-status.md` to `確認待ち`. Do not record human confirmation.
3. Return the created document paths, assumptions, unanswered questions, and the recommended first research prompt.
4. Stop. Do not conduct market research, select technology, or create application code in this mode during this prompt.

## Short prototype mode

When `進め方` is `短時間試作`, aim to reach executable validation within the confirmed time limit. The timebox constrains scope; it does not permit unverified claims or bypass safety decisions.

1. Create only the project documents needed to decide, build, and verify the primary flow. Record each skipped document, its reason, its effect, and the condition for creating it later in `docs/project-status.md`.
2. Treat kickoff confirmation as authorization for compact intermediate documents and one prototype implementation task inside the confirmed scope.
3. Check feasibility immediately. If the flow cannot reasonably reach validation in the timebox, reduce it to the smallest runnable learning slice and record deferred behavior. Ask only when materially different slices would change the intended outcome.
4. Keep research to at most two questions that can change the prototype decision. Prefer current primary sources. Use an explicit assumption only when research would consume implementation time and the choice is reversible.
5. Keep scope to one primary flow and no more than three `REQ` IDs. Record explicit exclusions.
6. Choose the simplest reversible design. Create an `ADR` only for a material choice. Do not add optional infrastructure, integrations, or abstractions.
7. Create one dependency-ready `TASK` with linked `REQ` and `TEST` IDs, observable acceptance criteria, excluded scope, and a focused validation command.
8. Use agent delegation under the HVE Lead's delegation rules to invoke `Implementation Engineer` after the task is dependency-ready. Wait for its result before proceeding. Preserve time for executable validation and final review; remove optional scope instead of skipping primary-flow tests.
9. After implementation and executable validation finish, use agent delegation to invoke `Quality Reviewer`. Require actual validation results, known limitations, skipped work, security and data notes, and requirement-to-test coverage.
10. Regardless of `確認方法`, set 最終確認 to `確認待ち` and show working behavior, commands and results, limitations, and the decision required from the user.

After each intermediate process, run a lightweight self-check and record assumptions and skipped work. With `最後にまとめて確認`, set the process to `仮完了` and continue; include all intermediate results in the consolidated final review. With `工程ごとに確認`, set the process to `入力待ち（HIL）`, show outputs and check results, and ask for approval or changes. On approval, mark the process `完了`, record the confirmation datetime, clear HIL, and start the next process. On requested changes, return it to `作業中`, record a new start datetime, apply the changes, and ask again.

Do not stop in `最後にまとめて確認` merely because an optional intermediate document is incomplete. Record the gap, protect the runnable primary flow, and carry it to final review. In `工程ごとに確認`, include the gap in the HIL confirmation and follow the user's decision.

Stop for HIL before production release, real confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or an irreversible design choice. Do not deploy to production in this prompt.

End with `次にすること`, `入力する内容`, `実行後に始まる作業`, and up to three `プロンプト候補` in plain Japanese.
