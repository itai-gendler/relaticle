---
kind: primary
routes:
  main: Edit record — task web
steps:
- text: Supply changes to the record’s own information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
- text: The Product saves supplied own values and preserves omitted configured values
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Title
    - Additional Values
    - Changed At
  contexts:
    main:
      place: customer-web::workspace::task
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Models/Task.php
---

# Edit record — task web

## Trigger

The actor requests this task operation through web.

## Outcome

The supplied information is retained and omitted configured values remain.

## Edge cases

- The collection board changes Status and Order. Native board saves do not establish action-path notification parity.
