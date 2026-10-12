---
kind: validation
routes:
  main: No workspace bound
steps:
- text: The request has no resolved working scope.
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
  target: app/Models/Scopes/WorkspaceScope.php
---

# No workspace bound

## Trigger

The request has no resolved workspace.

## Outcome

No CRM rows are returned; the global scope fails closed.
