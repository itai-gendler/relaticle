---
kind: validation
routes:
  main: Nonmember workspace switch
steps:
- text: The identity selects a working scope it neither owns nor belongs to.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Concerns/HasWorkspaces.php
---

# Nonmember workspace switch

## Trigger

The Account selects a workspace it neither owns nor belongs to.

## Outcome

Selection is refused; the persisted current workspace is unchanged.
