---
kind: primary
routes:
  main: Remove membership
steps:
- text: Confirm member removal
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product removes the addressed membership and clears its matching selection
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
  target: app/Models/Workspace.php
---

# Remove membership

## Trigger

The actor confirms removal of an ordinary workspace member.

## Outcome

The Membership is removed and the addressed Account is notified; its current selection is cleared if it was this workspace.
