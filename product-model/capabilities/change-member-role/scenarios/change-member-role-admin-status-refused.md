---
kind: validation
routes:
  main: Admin status change refused
steps:
- text: An Admin requests a role change whose old or new role is Admin.
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
  target: app/Actions/Jetstream/UpdateWorkspaceMemberRole.php
---

# Admin status change refused

## Trigger

An Admin requests a role change whose old or new role is Admin.

## Outcome

The change is refused and the existing role remains.
