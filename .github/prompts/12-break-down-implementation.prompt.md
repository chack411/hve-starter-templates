---
name: 12 Break Down Implementation
description: "Break an approved delivery milestone into small dependency-aware vertical-slice TASK artifacts with acceptance criteria, requirement links, and planned tests."
argument-hint: "Milestone or requirement IDs to decompose"
agent: Delivery Planner
---

Create implementation tasks for the requested approved milestone.

- Confirm the Delivery planning process is ready as `artifact-workflow` > `Start a Phase` defines. In `短時間試作`, also confirm the focused test plan exists.
- Use `docs/templates/implementation-task.md` for each task under `docs/delivery/tasks/TASK-NNN-short-title.md`.
- Prefer the smallest end-to-end user-visible or operationally verifiable slices.
- Link `REQ`, `ADR`, risk, and planned `TEST` IDs.
- Include scope exclusions, observable acceptance criteria, likely modules, dependencies, and narrow validation procedures.
- Update the traceability matrix and identify the first dependency-ready task.

In `短時間試作`, create one task for the primary flow unless a separate enabling task is unavoidable. The kickoff-confirmed scope authorizes that task for prototype implementation.

Do not implement tasks or create layer-only work unless it is an unavoidable enabling dependency.
