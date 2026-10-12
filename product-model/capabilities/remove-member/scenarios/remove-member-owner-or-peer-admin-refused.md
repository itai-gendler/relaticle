---
kind: validation
routes:
  main: Protected member removal
steps:
- text: An Admin requests removal of the owner or another Admin.
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
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Protected member removal

## Trigger

An Admin requests removal of the owner or another Admin.

## Outcome

The protected removal is refused; ownership and the protected membership remain.
