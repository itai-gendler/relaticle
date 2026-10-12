---
kind: validation
routes:
  main: Duplicate invitation
steps:
- text: The email is already a joined user or has an existing pending invitation.
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
  actor: workspace-admin
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/InviteWorkspaceMember.php
---

# Duplicate invitation

## Trigger

The email is already a workspace member or has an existing pending invitation.

## Outcome

Issuance returns the observed duplicate validation without another invitation.
