---
appliesTo:
- type: entity
  id: account
  effect: reads
  contexts:
  - place: customer-web::workspace::home
  - place: customer-web::workspace::create-workspace
  - place: customer-web::workspace::notifications
  - place: customer-web::workspace::export-records
permits:
- related:
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: has identity
    entity: workspace-member
- related:
  - verb: has identity
    entity: workspace-viewer
- unattended: true
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Accounts may read their own private information

Private identity, preferences and timezone are personal. The digest’s scheduled preference/timezone reads use its actual recipient Account and eligibility checks. Directory and roster disclosures have distinct selectors.
