---
appliesTo:
- type: entity
  id: reply
  effect: reads
permits:
- related:
  - verb: contains
    entity: conversation
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: contains
    entity: conversation
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: contains
    entity: conversation
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-member
- related:
  - verb: contains
    entity: conversation
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

# Only the owning Account may read personal replies

Reply disclosure follows the owning personal Conversation and its workspace.
