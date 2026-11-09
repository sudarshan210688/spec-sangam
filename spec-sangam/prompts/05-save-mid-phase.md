# Prompt 5 — Save mid-phase

Use when the context is filling up before a phase is finished.

```text
Pause PHASE <N>. Tick completed tasks in tasks.md. Append a caveman entry to progress.md marked IN-PROGRESS with the next unticked task id. Then stop.
```

Then run `/clear` and send:

```text
Resume PHASE <N>. Run the phase start ritual.
```

Claude resumes from the first unticked task and does not redo ticked ones.
