# Prompt 1 — Architecture.md (15 questions, one at a time)

Send after CLAUDE.md and progress.md exist in the project root. Replace the `<placeholders>` and edit the topic list to fit your project.

```text
Act as a <role, e.g. Solution Architect for agentic apps>.
Read CLAUDE.md and progress.md. <Optional: Read the reference project at <path> (READ-ONLY, no edits or deletes).>

Goal: produce Architecture.md for <project> by asking me 15 multiple-choice questions ONE AT A TIME.

For each question:
- 3–4 options (A–D), each with a 1–2 line explanation and trade-off
- Mark one "(Recommended)" with the reason; align recommendations with CLAUDE.md
- If my answer conflicts with CLAUDE.md, say so and ask whether to update CLAUDE.md
- Wait for my answer, then ask: "Confirm and proceed to Q<n+1>?" Continue only after I confirm

Topics, in order:
1  <data sources / inputs>
2  <scope cut: what is in and out>
3  <storage location and layout>
4  <data granularity>
5  <relationships between entities>
6  <duplicate detection / idempotency>
7  <trigger and UX for the main job>
8  <routing or classification>
9  <selection / retrieval>
10 <context assembly and token budget>
11 <LLM provider and model selection>
12 <output schema>
13 <evaluation of the output>
14 <persistence: files only vs database (apply YAGNI)>
15 <testing and docs per phase>

After Q15, write Architecture.md at the project root with:
purpose + example, scope lock, tech stack, folder structure, data model / schemas,
core flow, external services, API contract table, .env variables, phase list,
scaling notes, assumptions / open questions.

Do NOT write code. After Architecture.md, update progress.md (caveman), then STOP and wait for APPROVE.

Requirements:
- <requirement 1>
- <requirement 2>
- Backend APIs first, then frontend
- Apply YAGNI; approval-gated phases; README.md, Installation.md and the API collection updated after every phase
```

Reply `APPROVE` only after you have read the whole Architecture.md.
