---
kind: primary
routes:
  main: Omitted Task lists remain
steps:
- text: Supply a new title without collections
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product changes only the supplied own values
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
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

# Omitted Task lists remain

## Trigger

An update supplies Title but omits all relationship and assignee collections.

## Outcome

Title changes; existing Assignees, Companies, People and Opportunities remain.
