# Prompt 3 — tasks.md (one file, one section per phase)

Send after plan.md is approved.

```text
Read CLAUDE.md, progress.md, Architecture.md and plan.md. Create tasks.md at the project root.

Rules:
- One section per phase: "## PHASE <N> — <name>"
- Each section starts with a short context block (goal, files in scope, endpoints) so the phase can be built by reading only CLAUDE.md + progress.md + this section
- Each task is a small checkbox (one file or one endpoint):
  - [ ] T<N>.<k> <action> — done: <verifiable check>
- Group tasks under ### Build, ### Tests, ### Docs, ### Gate
- Each phase ends with a Gate block:
  - [ ] G<N>.1 typecheck clean; tests green
  - [ ] G<N>.2 manual verification (commands/requests and expected results)
  - [ ] G<N>.3 README.md, Installation.md and the API collection updated
  - [ ] G<N>.4 progress.md caveman entry appended, incl. verification results
  - [ ] G<N>.5 print "PHASE <N> COMPLETE. Reply APPROVE to start PHASE <N+1>: <name>." and STOP
- No task may build anything outside its phase scope (YAGNI)

No code. Update progress.md (caveman). STOP and wait for APPROVE.
```

See [../templates/tasks.md](../templates/tasks.md) for the shape.
