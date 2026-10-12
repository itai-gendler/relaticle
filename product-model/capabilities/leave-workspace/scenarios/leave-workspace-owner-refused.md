---
kind: validation
routes:
  main: Owner leave refused
steps:
- text: The owner reaches a leave request for their own working scope.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-owner
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Owner leave refused

## Trigger

The owner reaches a leave request for their own workspace.

## Outcome

The request is refused; the owner remains and ownership is unchanged.
