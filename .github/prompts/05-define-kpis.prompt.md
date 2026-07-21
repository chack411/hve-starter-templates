---
name: 05 Define KPIs
description: "Define decision-oriented KPIs with formulas, units, grain, sources, owners, baselines, targets, thresholds, and dashboard presentation."
argument-hint: "Optional business decisions or KPI areas to prioritize"
agent: Business Analyst
tools: [read, search, edit, vscode/askQuestions]
---

Define KPIs from the approved project brief and current-state analysis.

- Use `docs/templates/kpi-catalog.md` and save `docs/requirements/kpi-catalog.md`.
- Assign stable `KPI-NNN` IDs.
- For each KPI, define the decision supported, exact formula, unit, grain, time window, inclusions, exclusions, sources, owner, refresh, baseline, target, and visualization.
- Mark unavailable baselines or targets as provisional and create a validation action.
- Update the traceability matrix.

Do not create vanity metrics or imply that unavailable data exists.
