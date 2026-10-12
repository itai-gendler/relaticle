---
kind: primary
result: achieved
routes:
  main: Join as Member
steps:
- text: Confirm the addressed invitation
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::invitation-acceptance
  actor: workspace-member
  capability: accept-workspace-invitation
- text: The Product retains the assigned membership, removes the invitation and primes the joined Home context
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
  capability: accept-workspace-invitation
- text: Open the joined collection
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::tasks
  actor: workspace-member
  capability: browse-records
- text: The Product returns the Task collection in the joined scope
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Status
    - Priority
    - Due Date
  contexts:
    main:
      place: customer-web::workspace::tasks
  actor: workspace-member
  capability: browse-records
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

# Join as Member

## Trigger

A verified signed-in Account has a valid canonical-email-matching invitation whose issued role is Member.

## Outcome

The same Account holds Member in the joined Workspace, has selected it, and receives its Task collection after the explicitly primed Home hand-off.
