---
name: Source Code
description: "Use when creating or changing application source code for an approved implementation task."
applyTo: "src/**"
---

# Source Code Rules

- Require an approved `TASK-NNN` with linked requirements, acceptance criteria, and validation plan before editing. Require linked ADRs when a material design choice exists.
- In `短時間試作`, treat a task inside the kickoff-confirmed primary flow as approved for prototype implementation when its `REQ`, `TASK`, and `TEST` links, excluded scope, and validation command are explicit.
- Implement one task at a time and preserve its excluded scope.
- Follow existing local patterns and approved technology decisions; avoid unrelated refactors or dependencies.
- Validate inputs and authorization at the owning boundary and avoid exposing sensitive data in logs or errors.
- Add observable behavior needed to diagnose task failures without recording secrets.
- Make the smallest behavior-complete change and run the narrowest relevant executable validation immediately.
- When the first application task adds runnable source under `src/`, replace the placeholder in `src/README.md` with application-specific documentation. On later tasks, update it whenever behavior, module layout, architecture, prerequisites, configuration, or commands change.
- Keep `src/README.md` grounded in the implemented application. Include its purpose and scope, directory and module structure, implemented architecture and data flow, runtime prerequisites, safe configuration guidance, setup, run, build, lint, test, primary-use, and troubleshooting instructions. Verify paths against the source tree and commands against package scripts or build configuration, then run every documented command that applies. Record only commands that were actually verified, label planned but unimplemented behavior explicitly, and write `該当なし` with a reason when the app has no build, lint, or other listed command.
- Record changed files, commands, results, and residual risk in the task artifact.
