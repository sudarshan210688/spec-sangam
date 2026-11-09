# Architecture.md — <Project name>

> Status: DRAFT. Written by Claude from the 15-question interview (prompts/01-architecture.md). Change to APPROVED only after the human approves.

## 1. Purpose
<What the system does, for whom, and why.>

**Example**
```
Input:  <a realistic input>
Output: <what the system returns for it>
```

## 2. Scope lock
| Item | In scope | Out of scope |
|---|---|---|
| <area> | <included> | <excluded> |

## 3. Tech stack
| Layer | Choice |
|---|---|
| Backend | <…> |
| Frontend | <…> |
| Data | <…> |
| Validation | <…> |
| AI / models | <…> (IDs from .env) |
| Tests | <…> |

## 4. Folder structure
```
<project>/
  ...
```

## 5. Data model / schemas
<Entities, fields and validation rules.>

## 6. Core flow
<Step-by-step: input → processing → output. One subsection per step.>

## 7. External services
<Each API or model, what it is used for, limits, failure handling.>

## 8. API contract
| Method | Route | Request | Response |
|---|---|---|---|
| GET | `/api/health` | — | `{ status: "ok" }` |

Errors: `400` validation · `404` unknown · `502` upstream failure.

## 9. Environment variables
```
PORT=
<NAME>=     # what it controls, default
```

## 10. Phases (approval-gated)
| Phase | Name | Deliverable |
|---|---|---|
| P0 | Scaffold | <…> |
| P1 | <…> | <…> |

## 11. Scaling notes
<What changes when the data or traffic grows 10× or 100×. Not built now (YAGNI).>

## 12. Assumptions and open questions
1. <assumption to verify, and in which phase>
