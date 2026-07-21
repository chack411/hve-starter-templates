---
name: deliverable-quality-gate
description: "Review phase deliverables or implementation evidence for completeness, consistency, source quality, traceability, risk, and validation. Use for PASS, CONDITIONAL, or FAIL gate decisions."
argument-hint: "Phase name or TASK-NNN"
---

# Deliverable Quality Gate

This is a read-only review procedure. The reviewer reports defects and evidence; the user owns approval.

## Common Checks

1. Required artifacts exist and preserve mandatory template sections.
2. Approved upstream inputs are used without silent contradiction.
3. Facts, inferences, assumptions, recommendations, and open questions are distinguishable.
4. Stable IDs resolve in both directions and orphan checks are complete.
5. Critical risks have owners, responses, triggers, and verification.
6. Claims of completion are supported by reviewable evidence.

## 4-Hour Prototype Review

When `docs/project-status.md` selects `短時間試作`, review the prototype outcome using its `確認方法`. With `最後にまとめて確認`, review the consolidated outcome instead of failing each intermediate process for intentionally skipped documents. With `工程ごとに確認`, verify that each completed process has a recorded approval and that requested changes were resolved.

Require all of the following:

1. The kickoff-confirmed primary flow and exclusions are visible.
2. At least one `REQ`, `TASK`, and `TEST` connect the flow to actual validation evidence.
3. The focused validation command was executed and its real result is recorded.
4. Assumptions, skipped work, known limitations, and next risks are explicit.
5. No unresolved critical safety, security, privacy, compliance, destructive-operation, credential, or paid-resource decision is hidden.

For this mode:

- `PASS`: the primary flow meets its observable success check, validation passed, and no unresolved critical finding remains.
- `CONDITIONAL`: the primary flow was validated and is useful for learning, but documented non-critical limitations remain.
- `FAIL`: the primary flow is not runnable, required validation did not run or failed, evidence is fabricated or contradictory, or a critical safety condition remains.

Missing optional documents or broad coverage is not by itself a failure when the omission and impact are recorded. Do not lower the severity of security, privacy, data-loss, compliance, or fabricated-evidence findings.

## Phase Checks

### Research and Analysis

- Material claims have appropriate sources, dates, and confidence.
- Findings answer research questions and limitations are visible.
- Baselines have sources, units, periods, and owners.

### Product Definition

- Requirements trace to evidence and have observable acceptance criteria.
- Non-functional requirements are measurable.
- MVP inclusions and exclusions form a coherent outcome and have rationale.

### Architecture

- All approved MVP requirements have coverage.
- Material alternatives and trade-offs are compared.
- Security, data, operations, recovery, cost, migration, and proof activities are explicit.

### Delivery Planning

- Milestones have entry, exit, validation, and rollback criteria.
- MVP requirements map to dependency-ready tasks and planned tests.
- Estimates expose ranges and assumptions.

### Implementation

- Changes stay within approved task scope.
- Acceptance criteria have actual test or inspection evidence.
- Commands and results are recorded; skipped validation is not reported as passing.
- Documentation, task status, and traceability are updated.

## Severity

- **Critical**: unsafe outcome, fabricated evidence, approval bypass, or unrecoverable data/security risk.
- **High**: required artifact, acceptance evidence, major coverage, or decision rationale is missing.
- **Medium**: ambiguity or inconsistency that can materially affect implementation or verification.
- **Low**: localized clarity or maintainability issue with limited decision impact.

## Verdict

- `PASS`: exit criteria are met with no unresolved critical or high finding.
- `CONDITIONAL`: only explicit non-critical actions remain, with owners and due conditions.
- `FAIL`: required evidence, coverage, consistency, or validation is absent or contradictory.

List findings first, then coverage summary, verdict, required actions, and residual risks.
