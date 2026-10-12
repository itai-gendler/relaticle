---
kind: validation
routes:
  main: Invalid cursor
steps:
- text: The supplied pagination cursor is invalid.
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
  target: app/Queries/Concerns/ListsEntity.php
---

# Invalid cursor

## Trigger

The supplied pagination cursor is invalid.

## Outcome

Validation returns the cursor error rather than treating it as a valid continuation.
