# Prompt 4 — Start a phase

Run `/clear` first, so the new phase starts with an empty context. Then send:

```text
APPROVE. Run the phase start ritual for PHASE <N>.
```

Claude reads only CLAUDE.md and progress.md and prints five lines:

```text
done: P0–P<N-1>
last-decide: <last key decision>
issue: <open issues or none>
next: P<N> <name>
need: <files/sections to read>
```

If the summary is right, send:

```text
GO
```

Claude then reads only the `## PHASE <N>` section of tasks.md and builds.
If the summary is wrong, correct it before sending GO. A wrong summary means progress.md needs fixing.
