---
kind: primary
routes:
  main: Delete record — note rest
steps:
- text: Confirm deletion of the selected record
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
- text: The Product soft-deletes the record
  kind: product
  entities:
  - entity: note
    effect: changes
    facts: []
    from: Active
    to: Deleted
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/NotesController.php
---

# Delete record — note rest

## Trigger

The actor requests this note operation through rest.

## Outcome

The record leaves active reads and remains restorable. Independent linked CRM records remain. REST returns 204.
