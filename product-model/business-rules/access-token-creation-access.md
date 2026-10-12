---
appliesTo:
- type: entity
  id: access-token
  effect: creates
  to: Present
permits:
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-member
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
---

# Accounts may create their own authorized workspace token

The chosen Workspace is in the Account’s owned/joined set; name uniqueness, expiry and current-role grant clamping are checked.
