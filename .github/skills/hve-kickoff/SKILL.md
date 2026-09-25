---
name: hve-kickoff
description: "Start an HVE application project in 通常 or 短時間試作 mode, from kickoff through the mode-appropriate next step, and resume an unfinished kickoff or 短時間試作 run. Use when the user describes an app to build, asks to start a project or prototype, or answers an input wait raised during kickoff."
argument-hint: "課題、利用者、目的。わかれば進め方（通常/短時間試作）、制限時間、主な操作、成功の確認、行わないこと、確認方法"
---

# HVE Kickoff

This is the single kickoff procedure. `/hve-kickoff`, a plain request to the `Hyper Velocity Engineering Lead` agent, and `/00-start-project` all run it.

Run it inside the `Hyper Velocity Engineering Lead` agent, which owns delegation and keeps `src/` and `tests/` changes with the `Implementation Engineer`. If the current chat uses a different agent, tell the user in one sentence to select `Hyper Velocity Engineering Lead` and send the same request again, then stop.

Mode rules, state names, HIL handling, and time recording come from the `artifact-workflow` skill. This skill adds only the kickoff steps.

When resuming, read `docs/project-status.md` and continue from the first step that is not yet done instead of starting over.

## Done when

- `通常`: the kickoff documents exist, 開始準備 is `確認待ち`, and the user sees the first research prompt.
- `短時間試作`: the primary flow runs, its focused validation has been executed and recorded, the Quality Reviewer verdict is in, and 最終確認 is `確認待ち`.

## Common kickoff

1. Read `README.md`, `docs/project-status.md`, `docs/templates/project-brief.md`, and any existing project documents.
2. Take the mode from the user's words. If the user did not say `通常` or `短時間試作`, make the mode the first HIL choice rather than choosing it. Recommend `短時間試作` for a prototype or small MVP, and `通常` when durable decisions, broad evidence, or separate approvals matter more than a quick runnable result.
3. Ask only for what is missing to define the problem, users, desired outcome, scope, constraints, and success measures. For `通常`, also confirm the initial research questions. For `短時間試作`, also confirm the time limit, one primary user flow, its observable success check, explicit exclusions, and `確認方法`.
4. Fill in the HIL section of `docs/project-status.md`, then ask all missing items in one `askQuestions` call.
5. After the answer, record `進め方` and the mode-specific values, clear HIL, and continue in the same request.
6. Record the kickoff start and end times with `Record Execution Time`.

## 通常

1. Create `docs/project/project-brief.md`, `source-register.md`, `decision-log.md`, `risk-register.md`, and `traceability-matrix.md` from their templates.
2. Set 開始準備 to `確認待ち`. Do not record a person's confirmation.
3. Return the created paths, assumptions, unanswered questions, and the recommended first research prompt, then stop. Research, technology selection, and code start in later requests.

## 短時間試作

Follow `artifact-workflow` > `短時間試作` for scope limits, delegation, the time budget, the confirmation method, and safety stops. Kickoff confirmation authorizes the compact intermediate documents and one prototype implementation task inside the confirmed scope.

1. Create only the documents needed to decide, build, and verify the primary flow. Record each skipped document, its reason, its effect, and when to create it later in `docs/project-status.md`.
2. Check feasibility against the time limit. If the flow cannot reach validation in time, reduce it to the smallest runnable learning slice and record the deferred behavior. Ask only when materially different slices would change the intended outcome.
3. Send the research questions to `Market Researcher` in one request. When a question would cost implementation time and the choice is reversible, record an explicit assumption instead.
4. Write the compact current-state, requirement, design, and implementation-preparation documents yourself. Create an `ADR` only for a material choice.
5. Create one dependency-ready `TASK` with linked `REQ` and `TEST` IDs, observable acceptance criteria, excluded scope, and a focused validation command.
6. Delegate that task to `Implementation Engineer` and wait for its result.
7. Delegate the final review to `Quality Reviewer`. Require actual validation results, known limitations, skipped work, security and data notes, and requirement-to-test coverage.
8. Set 最終確認 to `確認待ち` and show the working behavior, commands and results, limitations, and the decision the user needs to make. Production deployment is out of scope for kickoff.

## Response

End with `次にすること`, `入力する内容`, `実行後に始まる作業`, and up to three `プロンプト候補` in plain Japanese.
