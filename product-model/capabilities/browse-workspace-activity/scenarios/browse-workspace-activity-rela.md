---
kind: primary
routes:
  main: Browse workspace activity — rela
steps:
- text: Request the change history
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
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
      place: customer-web::workspace::chat
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
---

# Browse workspace activity — rela

## Trigger

The actor requests cross-record history.

## Outcome

The workspace activity page includes actor, subject, field changes, source, time and import summaries. Rela pages at most 50 complete saves, default seven days and maximum 30; absent subjects are excluded.
