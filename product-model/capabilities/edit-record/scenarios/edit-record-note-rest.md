---
kind: primary
routes:
  main: Edit record — note rest
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::note
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: note
    effect: changes
    facts:
    - Title
    - Additional Values
    - Changed At
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

# Edit record — note rest

## Trigger

The actor requests this note operation through rest.

## Outcome

The supplied information is retained and omitted configured values remain.
