---
kind: primary
routes:
  main: Browse workspace activity — web
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-activity
  actor: workspace-admin
- text: The Product returns the scoped complete-save history
  kind: product
  entities:
  - entity: activity
    effect: reads
    facts:
    - Actor
    - Subject
    - Change
    - Source
    - Time
    - Import Summary
    - Workspace
  contexts:
    main:
      place: customer-web::workspace::workspace-activity
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Workspace/ActivityLog.php
---

# Browse workspace activity — web

## Trigger

The actor requests cross-record history.

## Outcome

The workspace activity page includes actor, subject, field changes, source, time and import summaries.
