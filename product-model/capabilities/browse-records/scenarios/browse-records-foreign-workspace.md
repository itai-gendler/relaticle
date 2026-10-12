---
kind: validation
routes:
  main: Foreign workspace requested
steps:
- text: "A request selects a working scope outside the identity\u2019s joined roles."
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
  target: app/Http/Middleware/SetApiWorkspaceContext.php
---

# Foreign workspace requested

## Trigger

A request selects a workspace outside the Account’s memberships.

## Outcome

Context binding refuses the request before returning CRM data.
