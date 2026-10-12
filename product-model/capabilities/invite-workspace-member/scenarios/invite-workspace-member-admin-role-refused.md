---
kind: validation
routes:
  main: Admin role refused
steps:
- text: An Admin selects the Admin role for a new invitation.
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

# Admin role refused

## Trigger

An Admin selects the Admin role for a new invitation.

## Outcome

The role request is refused; no Admin invitation is issued.
