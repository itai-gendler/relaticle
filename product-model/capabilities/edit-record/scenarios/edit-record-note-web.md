---
kind: primary
routes:
  main: Edit record — note web
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::note
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
      place: customer-web::workspace::note
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Note.php
---

# Edit record — note web

## Trigger

The actor requests this note operation through web.

## Outcome

The supplied information is retained and omitted configured values remain.
