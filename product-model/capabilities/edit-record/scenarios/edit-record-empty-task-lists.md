---
kind: primary
routes:
  main: Empty Task lists clear
steps:
- text: Supply empty collections
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::task
  actor: workspace-member
- text: The Product replaces supplied collections with empty lists
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Assignees
    - Companies
    - People
    - Opportunities
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

# Empty Task lists clear

## Trigger

An update explicitly supplies empty Task relationship and assignee lists.

## Outcome

Each supplied list is cleared, omitted lists remain, and linked records and Accounts are preserved.
