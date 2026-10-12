---
appliesTo:
- type: entity
  id: reply
  effect: changes
  facts:
  - Content
  - Response Outcome
  - Results
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

# The owning request may resolve its personal reply

Only request-attributed processing in the personal Conversation resolves the reply outcome; stopping visible streaming does not assert provider abortion.
