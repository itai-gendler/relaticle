---
kind: validation
routes:
  main: Invalid filter expression
steps:
- text: A supplied filter operator or field is outside the declared grammar.
  kind: condition
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Queries/EntityFilters.php
---

# Invalid filter expression

## Trigger

A supplied filter operator or field is outside the declared grammar.

## Outcome

Validation returns the filter error; no list mutation occurs.
