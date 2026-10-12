---
kind: primary
routes:
  main: Import activity summary
steps:
- text: Request working scope history
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-activity
  actor: workspace-admin
- text: The Product returns the displayed file process summary
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

# Import activity summary

## Trigger

The workspace contains recorded import activity.

## Outcome

Displayed history includes the import summary with its recorded source and outcome information.
