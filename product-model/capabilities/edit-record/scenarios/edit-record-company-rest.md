---
kind: primary
routes:
  main: Edit record — company rest
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::company
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
      place: rest-api::company
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Company.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/CompaniesController.php
---

# Edit record — company rest

## Trigger

The actor requests this company operation through rest.

## Outcome

The supplied information is retained and omitted configured values remain.
