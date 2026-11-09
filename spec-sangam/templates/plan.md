# plan.md — <Project name>

> Status: DRAFT. Source of truth: Architecture.md (approved <date>).
> One phase at a time; each ends at the approval gate.

## Conventions (all phases)
- Env vars are added in the phase that first uses them, not all in P0 (YAGNI).
- Every boundary is validated by a named schema.
- Tests cover deterministic code; network and model calls are checked manually or with the API collection.
- Every phase updates progress.md (caveman).

---

## P0 — Scaffold
**Goal:** <one sentence>

**Scope in:** <what is built>
**Scope out:** <what is deliberately NOT built (YAGNI)>

**Files:** <paths to create or change>

**API:**
| Method | Route | Request | Response |
|---|---|---|---|
| GET | `/api/health` | — | `{ status: "ok" }` |

**Acceptance:**
- <checkable statement with the command or request that proves it>

**Docs:** README (<what>) · Installation (<what>) · API collection (<what>) · progress.md

**Risks:** <what could go wrong and how it is handled>

---

## P1 — <name>
<same structure>

---

## Dependency order
```
P0 → P1 → P2 → …
```
| Phase | Depends on | Why |
|---|---|---|
| P1 | P0 | <reason> |

## Traceability — Architecture.md → phase
| Architecture § | Topic | Phase(s) |
|---|---|---|
| §1 | Purpose | <Pn> |
