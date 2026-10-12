---
kind: primary
routes:
  main: "Accept workspace invitation \u2014 already-member"
steps:
- text: Confirm acceptance of the addressed invitation
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-viewer
- text: The Product selects and primes the already joined Home context
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Current Workspace
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Http/Controllers/AcceptWorkspaceInvitationController.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/PendingInvitationsForUser.php
---

# Accept workspace invitation — already-member

## Trigger

A verified signed-in Account follows its matching valid invitation.

## Outcome

The matching already-member GET fast path persists the joined workspace selection and primes its Home destination without creating another Membership or consuming the still-valid invitation. The locked POST acceptance path separately handles concurrent already-member success and consumes a still-existing valid invitation.
