---
kind: primary
routes:
  main: Create record — opportunity web
steps:
- text: Supply new record information and optional references
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product retains the new record, optional links and configured values
  kind: product
  entities:
  - entity: opportunity
    effect: creates
    facts:
    - Name
    - Company
    - Point of Contact
    - Stage
    - Amount
    - Close Date
    - Order
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# Create record — opportunity web

## Trigger

The actor requests this opportunity operation through web.

## Outcome

A new active opportunity is retained and returned.
