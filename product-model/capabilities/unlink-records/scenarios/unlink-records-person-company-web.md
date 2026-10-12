---
kind: primary
routes:
  main: Unlink records — person-company web
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: person
    effect: changes
    facts:
    - Company
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::person
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/People/UpdatePeople.php
---

# Unlink records — person-company web

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Company link is cleared without deleting the linked record.
