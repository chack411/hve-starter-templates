---
name: 00 Fast Prototype
description: "Run the HVE workflow through a working prototype within a user-defined short timebox, with per-process or consolidated confirmation."
argument-hint: "Time limit, primary user, one flow, success check, exclusions, and confirmation method"
agent: Hyper Velocity Engineering Lead
tools: [read, search, edit, agent, todo, vscode/askQuestions]
---

Run the project in `短時間試作` mode. Aim to reach executable validation within the user-defined time limit. The timebox is a scope constraint, not permission to claim unrun work or bypass safety decisions.

1. Read `docs/project-status.md`, existing project documents, and repository patterns.
2. Before starting, confirm through `askQuestions` only what is missing: the time limit, primary user, one primary flow, its observable success check, explicit exclusions, and whether `確認方法` is `工程ごとに確認` or `最後にまとめて確認`. Record the question and resume prompt under `入力待ち（HIL）` first.
3. Set `進め方` to `短時間試作` and record the selected `確認方法`. Treat kickoff confirmation as authorization for compact intermediate documents and one prototype implementation task inside the confirmed scope.
4. Check feasibility immediately. If the flow cannot reasonably reach validation within the confirmed time limit, reduce it to the smallest runnable learning slice and record deferred behavior. Ask only when two materially different slices would change the intended outcome.
5. Run a lightweight self-check after each intermediate process and record assumptions and skipped documents. With `最後にまとめて確認`, set the process to `仮完了` and continue. With `工程ごとに確認`, set it to `入力待ち（HIL）`, show the outputs and check result, and ask for approval or changes before continuing. On approval, mark the process row `完了`, clear HIL, and set the overall status to the next process's `作業中`.
6. Keep research focused on at most two questions that can change the prototype. Prefer current primary sources, but use an explicit assumption when research would consume the implementation timebox and the choice is reversible.
7. Keep the product scope to one primary flow and no more than three `REQ` IDs. Record explicit exclusions.
8. Choose the simplest reversible design. Create an `ADR` only for a material choice. Do not add optional infrastructure, integrations, or abstractions.
9. Create one dependency-ready `TASK` with linked `REQ` and `TEST` IDs, observable acceptance criteria, excluded scope, and a focused validation command.
10. Delegate implementation to `Implementation Engineer`. Preserve enough time for executable validation and final review; remove optional scope rather than skipping primary-flow tests.
11. Delegate a final review to `Quality Reviewer`. Require actual validation results, known limitations, skipped work, security and data notes, and requirement-to-test coverage. With `最後にまとめて確認`, include all intermediate results in this consolidated review.
12. Regardless of `確認方法`, set 最終確認 to `確認待ち` and show the working behavior, commands and results, limitations, and the decision the user must make next.

Stop for HIL before production release, real confidential or personal data, regulated or safety-critical behavior, destructive operations, credentials, paid-resource creation, or an irreversible design choice. Do not deploy to production in this prompt.

With `最後にまとめて確認`, do not stop merely because an intermediate document is incomplete. Record the gap, protect the runnable primary flow, and carry it to final review. With `工程ごとに確認`, include the gap in the HIL confirmation and follow the user's decision.