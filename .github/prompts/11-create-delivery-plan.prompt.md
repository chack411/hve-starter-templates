---
name: 11 Create Delivery Plan
description: "Create a phased implementation roadmap with milestones, dependencies, estimate ranges, resources, risks, test strategy, release, rollback, and acceptance gates."
argument-hint: "Optional target date, team composition, capacity, or release constraints"
agent: Delivery Planner
---

Create a delivery plan from approved product and architecture artifacts.

- Confirm the Architecture process is ready as `artifact-workflow` > `Start a Phase` defines; otherwise stop with the missing criteria. In `短時間試作`, plan only the primary vertical slice.
- Save `docs/delivery/delivery-plan.md` from the delivery plan template.
- Save `docs/delivery/test-strategy.md` from the test strategy template.
- Use outcome-based milestones, dependency diagrams, estimate ranges with assumptions, resource gaps, release and rollback criteria, and risk responses.
- Map all MVP requirements to milestones and planned evidence.
- Update the risk register and traceability matrix. In `短時間試作`, create one focused test plan. End the process as `artifact-workflow` > `Complete a Phase` describes for the current mode.

Do not create implementation code or hide schedule uncertainty.
