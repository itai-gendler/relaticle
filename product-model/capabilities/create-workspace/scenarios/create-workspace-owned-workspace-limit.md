---
kind: validation
routes:
  main: Owned workspace limit reached
steps:
- text: The actual ownership relation count reaches the configured maximum, including scheduled deletions
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

# Owned workspace limit reached

## Trigger

The actual owned-workspace relation count reaches the configured maximum, default ten, including scheduled workspaces.

## Outcome

Creation is refused without retaining another workspace; invited memberships do not consume owned slots.
