---
kind: primary
routes:
  main: Delete record — opportunity rest
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunity
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts: []
    from: Active
    to: Deleted
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

# Delete record — opportunity rest

## Trigger

The actor requests this opportunity operation through rest.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain. REST returns 204.
