---
kind: validation
routes:
  main: Expired or revoked
steps:
- text: The invitation is expired or removed before the locked acceptance check, and the identity has not already
    joined.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
---

# Expired or revoked

## Trigger

The invitation is expired or removed before the locked acceptance check, and the Account has not already joined.

## Outcome

The observed no-longer-valid result is shown and no membership is created.
