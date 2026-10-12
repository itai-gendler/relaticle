---
appliesTo:
- type: entity
  id: access-token
  effect: reads
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
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-admin
  - verb: connects
    entity: ai-agent
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-member
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-member
  - verb: connects
    entity: ai-agent
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-viewer
- related:
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-viewer
  - verb: connects
    entity: ai-agent
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
---

# Accounts may read their own token information

Ordinary token settings disclose only personal token metadata. MCP context discloses the abilities of the actual current credential, not another token the Account owns; the raw secret is not retained for disclosure.
