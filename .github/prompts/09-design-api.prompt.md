---
name: 09 Design API
description: "Design an API contract for approved use cases, including resources, endpoints, schemas, authorization, errors, pagination, limits, compatibility, telemetry, and AI or integration consumers."
argument-hint: "Optional consumers, use cases, protocols, or compatibility constraints"
agent: Solution Architect
tools: [read, search, edit, vscode/askQuestions]
---

Design the API surface required by approved requirements and architecture.

- Use `docs/templates/api-design.md` and save `docs/architecture/api-design.md`.
- Identify consumers and map every operation to `REQ-NNN`.
- Define resource ownership, methods, paths, request and response schemas, authorization, errors, pagination, filtering, rate limits, idempotency, caching, audit, and telemetry.
- Include the authentication sequence in Mermaid and an evolution/deprecation policy.
- Record contract or security uncertainties as risks or proof activities.
- Update traceability.

Do not add speculative endpoints or generate server code.
