---
name: 11 Create Delivery Plan
description: "Create a phased implementation roadmap with milestones, dependencies, estimate ranges, resources, risks, test strategy, release, rollback, and acceptance gates."
argument-hint: "Optional target date, team composition, capacity, or release constraints"
agent: Delivery Planner
tools: [read, search, edit, vscode/askQuestions]
---

Create a delivery plan from approved product and architecture artifacts.

- In `通常`, verify the Architecture process is approved; otherwise stop with missing criteria. In `短時間試作`, accept `仮完了` with `最後にまとめて確認` or `完了` with `工程ごとに確認`, and plan only the primary vertical slice.
- Save `docs/delivery/delivery-plan.md` from the delivery plan template.
- Save `docs/delivery/test-strategy.md` from the test strategy template.
- Use outcome-based milestones, dependency diagrams, estimate ranges with assumptions, resource gaps, release and rollback criteria, and risk responses.
- Map all MVP requirements to milestones and planned evidence.
- In `通常`, update project status, risk register, and traceability matrix to `確認待ち` without recording human confirmation. In `短時間試作`, create one focused test plan. With `最後にまとめて確認`, set this process to `仮完了` and continue. With `工程ごとに確認`, set it to `入力待ち（HIL）` and continue only after explicit approval marks it `完了`.

Do not create implementation code or hide schedule uncertainty.
