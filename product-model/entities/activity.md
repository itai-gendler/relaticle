---
references:
- kind: code
  role: implementation
  target: app/Models/ActivityLog/Activity.php
---

# Activity

A displayed account of who changed a subject, what changed, through which source and when; import summaries are displayed with it.

## Information kept

- **Actor** — The retained actor.
- **Subject** — The retained subject.
- **Change** — The retained change.
- **Source** — The retained source.
- **Time** — The retained time.
- **Import Summary** — The retained import summary.
- **Workspace** — The workspace to which this instance belongs.

## States

### Recorded

The activity is recorded.
