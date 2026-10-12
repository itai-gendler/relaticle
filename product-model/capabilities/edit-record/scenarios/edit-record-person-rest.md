---
kind: primary
routes:
  main: Edit record — person rest
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::person
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: person
    effect: changes
    facts:
    - Name
    - Additional Values
    - Changed At
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

# Edit record — person rest

## Trigger

The actor requests this person operation through rest.

## Outcome

The supplied information is retained and omitted configured values remain.
