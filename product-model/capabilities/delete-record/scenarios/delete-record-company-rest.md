---
kind: primary
routes:
  main: Delete record — company rest
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::company
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: company
    effect: changes
    facts: []
    from: Active
    to: Deleted
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

# Delete record — company rest

## Trigger

The actor requests this company operation through rest.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain. REST returns 204.
