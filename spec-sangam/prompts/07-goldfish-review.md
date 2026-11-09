# Prompt 7 — Fresh-context spec review (Goldfish, optional)

Borrowed from Google's [Elephant–Goldfish Model](https://github.com/google/elephant-goldfish-model): a reviewer with **no memory of the conversation** finds the gaps that the author, who knows what they meant, reads past.

Run it after tasks.md is written and before you approve it. Use a **new session** (or a subagent) so the reviewer has no prior context.

```text
You have no prior context for this project. Read only CLAUDE.md, Architecture.md, plan.md and tasks.md. Review the plan as a fresh reviewer. Report:
1. Contradictions between the three files
2. Anything a developer would have to guess (unstated assumptions, vague terms)
3. Acceptance criteria that cannot be verified with a command, request or test
4. Requirements in Architecture.md with no phase or task covering them
5. Phases that depend on something built later
For each finding give file, section, the problem and a suggested fix. Fix nothing. Report only.
```

Take the findings back to the original session, decide which to accept, and approve the updated files.

Note: approving the plan yourself is the **human gate**, not the Goldfish. The Goldfish is a separate reviewer with a clean context.
