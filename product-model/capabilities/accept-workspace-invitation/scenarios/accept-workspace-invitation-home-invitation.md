---
kind: primary
routes:
  main: "Accept workspace invitation \u2014 home-invitation"
steps:
- text: Confirm acceptance of the addressed invitation
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
- text: The Product retains the join result and carries the actor to the joined working scope Home
  kind: product
  entities:
  - entity: membership
    effect: creates
    facts:
    - Account
    - Workspace
    - Role
    to: Active
  - entity: workspace-invitation
    effect: removes
    from: Issued
  - entity: account
    effect: changes
    facts:
    - Current Workspace
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-member
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

# Accept workspace invitation — home-invitation

## Trigger

A verified signed-in Account follows its matching valid invitation.

## Outcome

The addressed role membership is retained when absent, the invitation is removed, and the joined workspace becomes the persisted selection. The customer tenant is explicitly primed before joined-workspace Home. Concurrent already-member acceptance remains a success rather than duplicating membership.
