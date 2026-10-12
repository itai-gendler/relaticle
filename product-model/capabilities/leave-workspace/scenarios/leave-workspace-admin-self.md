---
kind: primary
routes:
  main: Leave as Admin
steps:
- text: Confirm leaving this working scope
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product removes the acting membership and clears matching selection
  kind: product
  entities:
  - entity: membership
    effect: removes
    from: Active
  - entity: account
    effect: changes
    facts:
    - Current Workspace
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/WorkspaceMembers.php
---

# Leave as Admin

## Trigger

The Admin uses the offered self-leave control in Members.

## Outcome

Its Membership is removed and matching current selection cleared. The source redirects, but a usable remaining-workspace destination is not asserted.
