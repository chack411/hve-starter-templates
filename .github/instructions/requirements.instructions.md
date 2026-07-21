---
name: Requirements Artifacts
description: "Use when writing KPIs, product requirements, user stories, acceptance criteria, non-functional requirements, MVP scope, or prioritization."
applyTo: "docs/requirements/**"
---

# Requirements Artifact Rules

- Assign stable `KPI-NNN`, `REQ-NNN`, or `REQ-NFR-NNN` IDs and never renumber them.
- Link each requirement to an insight, problem, KPI, constraint, or explicit assumption.
- Write observable acceptance criteria covering normal, error, boundary, authorization, and data behavior as applicable.
- Make non-functional requirements measurable and name the verification method.
- Define inclusions and exclusions; do not hide architecture choices inside requirements unless they are approved constraints.
- Record scoring evidence and uncertainty for MVP decisions.
- Update `docs/project/traceability-matrix.md` for every tracked addition or change.
