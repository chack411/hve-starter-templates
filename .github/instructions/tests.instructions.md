---
name: Tests
description: "Use when creating or changing automated tests, fixtures, test data, contract tests, integration tests, or end-to-end tests."
applyTo: "tests/**"
---

# Test Rules

- Link tests to `TEST-NNN`, `TASK-NNN`, and `REQ-NNN` in names, metadata, or the task evidence as the selected framework permits.
- Cover observable normal, error, boundary, authorization, concurrency, and recovery behavior required by acceptance criteria.
- Prefer deterministic tests with isolated data and controlled time, locale, randomness, and external dependencies.
- Never use production secrets or copied sensitive production data.
- Assert outcomes and contracts rather than private implementation details.
- Do not weaken existing tests to make a change pass.
- Record the exact command and result; skipped or unavailable checks are not passes.
