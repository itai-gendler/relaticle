---
kind: primary
routes:
  main: Edit record — company web
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: company
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
---

# Edit record — company web

## Trigger

The actor requests this company operation through web.

## Outcome

The supplied information is retained and omitted configured values remain.
