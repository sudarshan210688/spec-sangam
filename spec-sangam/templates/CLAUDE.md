# CLAUDE.md — <Project name> (SpecSangam driver)

> Copy this file to your project root and replace every `<placeholder>`. Delete lines that don't apply.

## Project
<One or two sentences: what the project does and for whom.>

## Read order every session
1. CLAUDE.md  2. progress.md
Then follow the Phase start ritual. Read Architecture.md, plan.md and tasks.md only when the ritual or the current task needs them.
Use progress.md as working memory. Don't re-read source already summarized there unless the task needs it.

## Phase start ritual (mandatory before every phase)
On session start, after /clear, or after APPROVE:
1. Read CLAUDE.md and progress.md only.
2. Print a 5-line caveman summary:
   done: <phases completed>
   last-decide: <last key decision>
   issue: <open issues or none>
   next: P<N> <name>
   need: <files/sections to read for P<N>>
3. Wait for "GO" before reading tasks.md or any source file.
4. On GO: read only the PHASE <N> section of tasks.md, then implement.
If progress.md shows P<N> IN-PROGRESS: resume from the first unticked task in tasks.md for P<N>; do not redo ticked tasks.

## Hard rules
- <Optional: reference project path> is READ-ONLY. Never edit, move or delete anything there. Never read its .env files.
- Spec-first: no code until Architecture.md and plan.md are approved.
- One phase at a time. <Optional ordering rule, e.g. "Backend and APIs first; frontend only after all backend phases are approved.">
- Approval gate: at the end of each phase STOP and print:
  "PHASE <N> COMPLETE. Reply APPROVE to start PHASE <N+1>: <name>."
  Do not start the next phase without the word APPROVE.
- Never edit Architecture.md, plan.md or tasks.md without explicit approval.
- YAGNI: build only what the current task in tasks.md names. No speculative abstractions, no unused config, no database unless Architecture.md says so.
- Validate every boundary: env, request bodies, LLM structured output, files read from disk. <Name your validation library, e.g. Zod.>
- Secrets in .env only; keep .env.example updated with blank values. Never commit .env. Never read .env; use .env.example.
- Within a phase, work without asking for confirmation on routine steps (file edits, build, test, local requests). Ask only at the approval gate or when blocked.

## Tech stack
- <Backend>
- <Frontend>
- <Data / storage>
- <AI models or services, read from .env, never hardcoded>
- <Unit tests: what is tested and with what>
- <API tests: e.g. Postman collection>

## Scope lock
- <What is in scope>
- <What is explicitly out of scope>

## Project layout
```
<project>/
  CLAUDE.md  Architecture.md  plan.md  tasks.md  progress.md
  README.md  Installation.md
  <backend>/  <frontend>/  <tests>/  <api-collection>/
```

## End-of-phase checklist (all required before the gate)
- [ ] tasks.md items for this phase ticked
- [ ] Tests passing for this phase's code
- [ ] progress.md updated (caveman format)
- [ ] README.md updated (features, endpoints)
- [ ] Installation.md updated (setup, env vars, run commands)
- [ ] <API collection> updated with new endpoints, sample bodies and checks
- [ ] Endpoints manually verified; results noted in progress.md

## Context hygiene
- Between phases the user runs /clear, then sends: "APPROVE. Run the phase start ritual for PHASE <N>."
- If context fills mid-phase: append partial progress to progress.md marked IN-PROGRESS before the user clears.

## progress.md format (caveman: terse, no prose)
```
## P<N> <name> — DONE | IN-PROGRESS <YYYY-MM-DD>
did: <comma list>
files: <paths>
api: <METHOD route → status>
decide: <key decisions>
issue: <open issues or none>
next: P<N+1> <name>
```
