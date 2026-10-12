---
kind: primary
routes:
  main: Revoke outgoing invitation
steps:
- text: Confirm invitation revocation
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product removes the outgoing invitation
  kind: product
  entities:
  - entity: workspace-invitation
    effect: removes
    from: Issued
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RevokeWorkspaceInvitation.php
---

# Revoke outgoing invitation

## Trigger

The actor confirms revocation of an outgoing invitation.

## Outcome

The invitation is removed and its credential no longer joins the workspace.
