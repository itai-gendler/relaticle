---
kind: primary
routes:
  main: Decline incoming invitation
steps:
- text: Choose Decline
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
- text: The Product removes the selected incoming invitation
  kind: product
  entities:
  - entity: workspace-invitation
    effect: removes
    from: Issued
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/DeclineWorkspaceInvitation.php
---

# Decline incoming invitation

## Trigger

Home offers a current invitation matching the Account’s email.

## Outcome

The matching invitation is removed; membership and current-workspace selection are unchanged.
