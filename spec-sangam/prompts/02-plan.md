# Prompt 2 — plan.md

Send after Architecture.md is approved.

```text
Read CLAUDE.md, progress.md and the approved Architecture.md. Create plan.md at the project root.

plan.md must contain:
- Phases: <P0 scaffold, P1 …, P2 …, … last phase: E2E + final docs>
- Per phase:
  goal
  scope in / scope out (YAGNI — list what is deliberately NOT built)
  files to create/modify
  API endpoints (method, route, request/response schema names)
  acceptance criteria (verifiable with a command, request or test, with a sample request)
  docs to update (README, Installation, API collection, progress.md)
  risks
- Dependency order between phases
- A traceability table: Architecture.md section → phase

No code. Update progress.md (caveman). STOP and wait for APPROVE.
```

Before approving, check that every Architecture.md section appears in the traceability table.
