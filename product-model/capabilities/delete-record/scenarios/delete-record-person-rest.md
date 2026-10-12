---
kind: primary
routes:
  main: Delete record — person rest
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::person
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: person
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: rest-api::person
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/People.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/PeopleController.php
---

# Delete record — person rest

## Trigger

The actor requests this person operation through rest.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain. REST returns 204.
