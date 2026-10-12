---
kind: primary
routes:
  main: Unlink records — task-person rest
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - People
    - Changed At
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/UpdateTask.php
---

# Unlink records — task-person rest

## Trigger

The actor supplies a relationship change.

## Outcome

Specified entries are detached; other entries and linked records remain.
