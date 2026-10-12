---
kind: primary
routes:
  main: Link records — person-company web
steps:
- text: Choose the relationship entries to link
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

# Link records — person-company web

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Company link is retained.
