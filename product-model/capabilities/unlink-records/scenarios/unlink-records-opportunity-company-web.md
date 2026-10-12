---
kind: primary
routes:
  main: Unlink records — opportunity-company web
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Company
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/UpdateOpportunity.php
---

# Unlink records — opportunity-company web

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Company link is cleared without deleting the linked record. Company and Point of Contact are independent and need not refer to matching Companies; clearing one preserves the other.
