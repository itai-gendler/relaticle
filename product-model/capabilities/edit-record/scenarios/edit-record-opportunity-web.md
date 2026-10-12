---
kind: primary
routes:
  main: Edit record — opportunity web
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
---

# Edit record — opportunity web

## Trigger

The actor requests this opportunity operation through web.

## Outcome

The supplied information is retained and omitted configured values remain.

## Edge cases

- The collection board changes Stage and Order. Native board saves do not establish action-path notification parity.
