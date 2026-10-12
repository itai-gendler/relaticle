---
appliesTo:
- type: entity
  id: access-token
  effect: changes
  facts:
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
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

# Accounts may change their own clamped token grants

The token remains bound to its existing Workspace. Offered grants are intersected again with actual current authority.
