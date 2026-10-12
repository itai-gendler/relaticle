---
kind: primary
routes:
  main: Browse the administrative roster
steps:
- text: Open Members
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product returns the administrative working scope roster
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Email
  - entity: membership
    effect: reads
    facts:
    - Account
    - Workspace
    - Role
  - entity: workspace-invitation
    effect: reads
    facts:
    - Email
    - Role
    - Issued At
    - Expires At
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Workspace/Members.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/WorkspaceMembers.php
---

# Browse the administrative roster

## Trigger

The actor opens Members.

## Outcome

The owner, Membership role/name/email information and current outgoing invitations are available.
