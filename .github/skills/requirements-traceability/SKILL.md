---
name: requirements-traceability
description: "Create and maintain traceability across research insights, KPIs, requirements, architecture decisions, implementation tasks, and tests. Use for ID assignment, coverage checks, change impact, and orphan detection."
argument-hint: "Item or phase to trace"
---

# Requirements Traceability

## Stable IDs

| Type | Pattern | Meaning |
| --- | --- | --- |
| Insight | `INSIGHT-NNN` | Evidence-based research or analysis finding |
| KPI | `KPI-NNN` | Defined outcome or operating measure |
| Requirement | `REQ-NNN` | Functional requirement |
| Non-functional requirement | `REQ-NFR-NNN` | Measurable quality requirement |
| Architecture decision | `ADR-NNN` | Significant technical decision |
| Implementation task | `TASK-NNN` | Approved vertical slice |
| Test | `TEST-NNN` | Planned or implemented verification evidence |

IDs are permanent. Never renumber or reuse a retired ID.

## Required Links

- A requirement links to at least one insight, problem, KPI, constraint, or explicit assumption.
- An ADR links to requirements and quality attributes it addresses.
- An MVP requirement links to one or more tasks.
- A task links to requirements, applicable ADRs, risks, and planned tests.
- A test links to its task and requirements.

## Update Procedure

1. Select the next unused ID by inspecting artifacts and `docs/project/traceability-matrix.md`.
2. Add the item in its owning artifact.
3. Add or update the matrix row using IDs, not titles alone.
4. Check both forward and backward links.
5. Run orphan checks from the matrix template.
6. For an approved-item change, list affected downstream IDs and record the impact review.

## Gate Checks

- Product gate: no requirement lacks rationale and acceptance criteria.
- Architecture gate: every approved MVP requirement has design coverage or an explicit no-change rationale.
- Planning gate: every MVP requirement has a milestone, task, and planned evidence.
- Implementation gate: completed tasks have passing evidence and no unexplained requirement gaps.
