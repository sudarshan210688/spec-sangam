# SpecSangam (ஸ்பெக் சங்கம்)

**A lightweight, measured spec-driven development workflow for building software with Claude, one approved phase at a time.**

*Sangam* is Tamil for "coming together". In SpecSangam the specs, the human and Claude come together: the specs say what to build, Claude builds it, and the human approves every step.

This repo holds the templates and prompts I use. The token numbers below come from a real project built with it, [Clausario](https://github.com/sudarshan210688/Clausario).

---

## The five steps

| # | Step | Output | Gate |
|---|---|---|---|
| 1 | **Interview**: Claude asks 15 multiple-choice questions, one at a time, each with a recommended option and trade-offs | Architecture.md | You approve each answer, then the file |
| 2 | **Plan**: phases with scope in/out, files, endpoints, acceptance criteria, risks and a traceability table | plan.md | APPROVE |
| 3 | **Tasks**: one file, one `## PHASE N` section per phase, small checkable tasks, a gate block at the end of each phase | tasks.md | APPROVE |
| 4 | **Build one phase**: `/clear`, phase start ritual, 5-line summary, `GO`, Claude reads only that phase's section and builds | code, tests, docs | GO |
| 5 | **Verify and hand off**: tests, manual checks, README / Installation / API collection updated, caveman entry in progress.md | progress.md | APPROVE before the next phase |

Steps 4 and 5 repeat for every phase.

## Four practices

1. **Approval gates.** Claude stops at the end of every phase and prints `PHASE N COMPLETE. Reply APPROVE to start PHASE N+1`. Nothing moves without the word APPROVE.
2. **YAGNI.** Every phase in plan.md lists what is deliberately *not* built. Claude builds only what the current task names.
3. **Caveman progress.md.** Terse lines (`did:`, `files:`, `api:`, `decide:`, `issue:`, `next:`). It is the working memory between sessions, so it is kept short: it is read at the start of every session. (My own terse format; not related to the caveman plugin.)
4. **Docs every phase.** README.md, Installation.md and the API collection are updated before each gate, not at the end.

## Why it saves tokens

At the start of a phase Claude reads only CLAUDE.md, progress.md and that phase's section of tasks.md, instead of every spec file.

Measured on [Clausario](#where-it-came-from), at the start of every phase:

| Phase being started | Read all spec files (without SpecSangam) | SpecSangam phase start (with SpecSangam) | This phase's tasks only (part of the SpecSangam total) | Fewer spec tokens |
|---|---:|---:|---:|---:|
| P0 | 26,516 | 4,565 | 838 | 83% |
| P1 | 26,964 | 6,023 | 1,848 | 78% |
| P2 | 28,548 | 6,567 | 808 | 77% |
| P3 | 30,413 | 8,249 | 625 | 73% |
| P4 | 31,430 | 9,433 | 792 | 70% |
| **P5** | **32,916** | **11,099** | **972** | **66%** |
| P6 | 34,432 | 12,167 | 524 | 65% |
| P7 | 35,740 | 13,554 | 603 | 62% |
| P8 | 37,274 | 14,899 | 414 | 60% |

All numbers are tokens. "This phase's tasks only" is already included in the SpecSangam total; it shows how small one phase's section is.

**Example: the Phase 5 start, file by file**

| File | Without SpecSangam | With SpecSangam |
|---|---:|---:|
| CLAUDE.md | 3,000 | 3,000 |
| progress.md (notes from P0–P4) | 7,127 | 7,127 |
| Architecture.md | 7,995 | not read |
| plan.md | 7,228 | not read |
| tasks.md | 7,566 (all 9 phases) | 972 (Phase 5 section only) |
| **Total** | **32,916** | **11,099** |

Saving = 1 − (11,099 ÷ 32,916) = 1 − 0.34 = **about 66% fewer spec tokens**.

**How it was measured**
1. The real spec files from Clausario (CLAUDE.md, Architecture.md, plan.md, tasks.md, progress.md).
2. For each phase, progress.md is counted only up to the entries written before that phase started.
3. Read all spec files = CLAUDE.md + Architecture.md + plan.md + all of tasks.md + progress.md.
4. SpecSangam phase start = CLAUDE.md + progress.md + only that phase's `## PHASE N` section of tasks.md.
5. Fewer spec tokens = 1 − (SpecSangam phase start ÷ read all spec files).

**Limits**
- Counted with the `o200k_base` tokenizer (js-tiktoken) as an approximation; Claude's tokenizer gives different absolute numbers.
- Spec files only. The system prompt, source code, conversation and output are not included, so this is the saving on spec reading, not on the whole session.
- The baseline is "read every spec file", not "no workflow".
- These are the files the phase start ritual tells Claude to read. Check what is actually loaded with `/context` in Claude Code after `GO`.
- The saving falls from 83% to 60% because progress.md grows every phase. Keep it caveman-short.

## Quick start

1. Copy [`templates/CLAUDE.md`](templates/CLAUDE.md) and [`templates/progress.md`](templates/progress.md) into your project root and fill in the placeholders.
2. Open Claude Code in the project and send [Prompt 1](prompts/01-architecture.md). Answer the 15 questions. Approve Architecture.md.
3. Send [Prompt 2](prompts/02-plan.md). Approve plan.md.
4. Send [Prompt 3](prompts/03-tasks.md). Approve tasks.md.
5. *(Optional)* Run the [fresh-context review](prompts/07-goldfish-review.md) in a new session and fix what it finds.
6. For each phase: `/clear` → [Prompt 4](prompts/04-start-phase.md) → check the summary → `GO` → build → [Prompt 6](prompts/06-end-of-phase-check.md) → `APPROVE`.
7. If the context fills mid-phase, use [Prompt 5](prompts/05-save-mid-phase.md).

## Files

```
spec-sangam/
  README.md
  templates/
    CLAUDE.md          rules, phase start ritual, gate text, checklist
    Architecture.md    skeleton filled in by the 15-question interview
    plan.md            phase skeleton with scope out, acceptance, traceability
    tasks.md           one section per phase with a gate block
    progress.md        caveman log
  prompts/
    01-architecture.md
    02-plan.md
    03-tasks.md
    04-start-phase.md
    05-save-mid-phase.md
    06-end-of-phase-check.md
    07-goldfish-review.md
  docs/
    SpecSangam-carousel.pdf
```

## Where it came from

SpecSangam was used to build **Clausario**, a learning project that maps user stories to GDPR and EU AI Act articles and generates test scenarios. It was built in nine approved phases (P0–P8):
[github.com/sudarshan210688/Clausario](https://github.com/sudarshan210688/Clausario).

## Built on

SpecSangam is not the first spec-driven workflow. It builds on ideas these projects made popular:

| Work | Idea | What SpecSangam does differently |
|---|---|---|
| [GitHub Spec Kit](https://github.com/github/spec-kit) | Spec-first steps: specify, plan, tasks, implement | Plain markdown files and prompts, no CLI |
| [Kiro](https://kiro.dev) | Requirements, design and tasks files in the editor | Works in any Claude Code project |
| [GSD (Get Shit Done)](https://github.com/gsd-build/get-shit-done) | Phases, a state file, fresh context per plan | One tasks.md section per phase, read only after GO |
| [Harper Reed's LLM codegen workflow](https://harper.blog/2025/02/16/my-llm-codegen-workflow-atm/) | "Ask me one question at a time" to build a spec | 15 multiple-choice questions, each with a recommended option and trade-offs |
| [Anthropic: effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | A progress file a new session reads to get its bearings | Caveman progress.md plus a 5-line summary before GO |
| [Google's Elephant–Goldfish Model](https://github.com/google/elephant-goldfish-model) | Fresh-context reviewers | Optional review prompt (Prompt 7) |

What SpecSangam adds: a human gate after every phase, docs updated at every gate, and [measured token numbers](#why-it-saves-tokens) with the method and limits.

## SpecSangam and the Elephant–Goldfish Model

Google's [Elephant–Goldfish Model (EGM)](https://github.com/google/elephant-goldfish-model) is a different approach to the same problem: an "Elephant" agent drafts with full context, and "Goldfish" reviewer agents with fresh context check the draft before a human approves it.

| | EGM | SpecSangam |
|---|---|---|
| Who drafts | Elephant agent with full context | Claude, from 15 approved answers |
| Who reviews | Goldfish agents with fresh context | The human, at every gate (fresh-context review is optional, Prompt 7) |
| Spec artifacts | concepts brief, design draft, design docs | Architecture.md, plan.md, tasks.md |
| Build unit | per design | one phase at a time, one tasks.md section |
| Memory between sessions | the design docs | caveman progress.md + phase start ritual |
| Human role | approves the reviewed design | approves each answer, each spec file and every phase |

SpecSangam is my own workflow and is not affiliated with Google or EGM. Prompt 7 borrows the Goldfish idea.

## Notes

- The templates assume a project with an API (endpoints, an API collection, typecheck and tests at each gate). For a script, notebook or UI-only project, delete the lines that don't apply.
- Made for Claude Code; the prompts are plain text and work with other coding agents that read a project instructions file.
- Built for learning. Clausario is for educational use only and is not legal advice.
- Never put secrets in CLAUDE.md, progress.md or `.env.example`. The templates tell Claude never to read `.env`.

---

© 2026 Sudarshan Ramanujam.
