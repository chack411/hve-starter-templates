---
name: 00 Start Project
description: "Initialize a new research-driven application project with a project brief, cross-project registers, research questions, and project status."
argument-hint: "Describe the business problem, target users, constraints, and desired outcome"
agent: Hyper Velocity Engineering Lead
tools: [read, search, edit, vscode/askQuestions]
---

Initialize this repository for the application described by the user.

1. Read `README.md`, `docs/project-status.md`, and `docs/templates/project-brief.md`.
2. Determine whether the user wants `通常` or `短時間試作`. Recommend `短時間試作` for a prototype or small MVP. Ask only for missing information needed to define the problem, users, scope, constraints, success measures, and initial research questions. Before asking, set `docs/project-status.md` to `入力待ち（HIL）` and fill in what to answer, answer examples or choices, what starts after the answer, and a resume prompt. Use `askQuestions`.
3. Create `docs/project/project-brief.md`, `source-register.md`, `decision-log.md`, `risk-register.md`, and `traceability-matrix.md` from their templates.
4. In `通常`, set the 開始準備 row in `docs/project-status.md` to `確認待ち`. In `短時間試作`, direct the user to `/00-fast-prototype` so kickoff confirmation can capture the time limit, scope, and `確認方法`. Do not record human confirmation.
5. After the answer, clear the HIL entry and continue. Return the created document paths, assumptions, unanswered questions, and the recommended first research prompt.

End with `次にすること`, `入力する内容`, `実行後に始まる作業`, and up to three `プロンプト候補` in plain Japanese.

Do not conduct market research, select technology, or create application code in this step.
