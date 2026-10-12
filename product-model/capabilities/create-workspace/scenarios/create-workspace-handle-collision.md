---
kind: validation
routes:
  main: Requested handle conflicts
steps:
- text: The explicitly supplied handle is invalid or already used.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::create-workspace
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::create-workspace
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::create-workspace
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
---

# Requested handle conflicts

## Trigger

The explicitly supplied handle is invalid or already used.

## Outcome

Validation reports the handle error and no workspace is created; a missing handle is settled during insertion.
