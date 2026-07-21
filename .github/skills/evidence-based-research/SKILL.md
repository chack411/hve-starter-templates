---
name: evidence-based-research
description: "Conduct evidence-based market, competitor, alternative, pricing, adoption, or industry research. Use when external claims need current primary sources, URLs, dates, confidence, conflict handling, and a source register."
argument-hint: "Research question and decision to support"
---

# Evidence-Based Research

Use this workflow for external research that informs product or architecture decisions.

## Inputs

- A bounded research question and decision it supports
- Geography, segment, time horizon, and constraints
- `docs/project/project-brief.md`
- Existing `docs/project/source-register.md`

## Procedure

1. Decompose the question into claims that would change the decision.
2. Define consistent comparison criteria before collecting options.
3. Search broadly to discover terminology and likely primary sources.
4. Verify material claims using original documentation, standards, filings, regulatory material, datasets, or research where available.
5. For every source, capture title, publisher, URL, source type, published/updated date, access date, supported insight IDs, and confidence.
6. Triangulate decision-critical claims. Record disagreement and explain which source is stronger and why.
7. Assign `INSIGHT-NNN` IDs and separate:
   - verified fact
   - inference from cited facts
   - assumption requiring validation
   - recommendation based on stated criteria
8. Write the report using `docs/templates/research-report.md` and update the source register.
9. Run the completion checklist and report unanswered questions.

## Confidence

- **High**: current primary evidence directly supports the claim and is independently corroborated when practical.
- **Medium**: credible evidence is indirect, older, or supported by only one source.
- **Low**: evidence is promotional, anecdotal, methodologically unclear, stale, or materially disputed.

See [source quality](./references/source-quality.md) for selection and conflict rules.

## Stop Conditions

Stop and label the gap when access is unavailable, source dates cannot be verified, the question depends on private organizational facts, or evidence is insufficient. Never fill a gap with a plausible citation or metric.

## Output Contract

Return the report path, source-register changes, insights by ID, confidence and limitations, conflicting evidence, and decisions the report can support. Do not convert findings directly into approved requirements.
