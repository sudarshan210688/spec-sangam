# tasks.md — <Project name>

> Derived from plan.md (approved <date>) and Architecture.md. One PHASE section per approval gate.
> Format: `- [ ] T<phase>.<n> <action> — done: <check>`. Tick `[x]` when done. Resume from the first unticked task.
> Every phase ends with the gate block (G tasks). Never start the next phase without APPROVE.

---

## PHASE 0 — Scaffold
goal: <one line>
files: <paths in scope>
endpoints: <routes added in this phase, or none>

### Build
- [ ] T0.1 <small action, one file or one endpoint> — done: <verifiable check>
- [ ] T0.2 <…> — done: <…>

### Tests
- [ ] T0.3 <test file and what it covers> — done: tests green

### Gate
- [ ] G0.1 Typecheck clean; tests green
- [ ] G0.2 Manual: <requests or commands to run and expected results>
- [ ] G0.3 README.md, Installation.md and the API collection updated
- [ ] G0.4 progress.md `## P0 Scaffold — DONE` (caveman) incl. verification results
- [ ] G0.5 Print `PHASE 0 COMPLETE. Reply APPROVE to start PHASE 1: <name>.` and STOP

---

## PHASE 1 — <name>
goal: <…>
files: <…>
endpoints: <…>

### Build
- [ ] T1.1 <…> — done: <…>

### Gate
- [ ] G1.1 … (same gate block as above)
