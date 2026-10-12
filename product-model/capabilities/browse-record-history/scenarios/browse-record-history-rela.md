---
kind: primary
routes:
  main: Browse record history — rela
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
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
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
---

# Browse record history — rela

## Trigger

The actor requests one-record history.

## Outcome

The active visible selected record’s change history is returned. A soft-deleted or missing selected subject returns the traced not-found result; cross-record queries separately retain deleted-but-present subject activity. Rela pages at most 50 complete saves, default seven days and maximum 30; absent subjects are excluded.
