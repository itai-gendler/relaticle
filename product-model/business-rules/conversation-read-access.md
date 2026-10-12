---
appliesTo:
- type: entity
  id: conversation
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
  target: packages/Chat/src/Http/Controllers/ChatController.php
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationsQuery.php
---

# Only the owning Account may read a personal Chat

The selected personal owner and workspace are checked. The current workspace alone does not expose another Account’s transcript.
