---
kind: primary
routes:
  main: Edit record — opportunity rest
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
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
      place: rest-api::opportunity
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Opportunity.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/OpportunitiesController.php
---

# Edit record — opportunity rest

## Trigger

The actor requests this opportunity operation through rest.

## Outcome

The supplied information is retained and omitted configured values remain.
