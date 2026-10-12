---
kind: primary
routes:
  main: Browse record history — web
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-viewer
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
      place: customer-web::workspace::opportunity
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Workspace/ActivityLog.php
---

# Browse record history — web

## Trigger

The actor requests one-record history.

## Outcome

The visible selected record’s change history is returned, including deleted-but-retained subject history where traced.
