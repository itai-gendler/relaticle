---
appliesTo:
- type: entity
  id: conversation
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
  target: packages/Chat/src/Http/Controllers/ChatController.php
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationsQuery.php
---

# An Account may create its own personal Chat

First-send retention and eligible personal setup-chat initialization use the actual Account and resolved workspace; hosted/model/credit gates apply to the request.
