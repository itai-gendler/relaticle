---
appliesTo:
- type: entity
  id: custom-field-creation-proposal
  effect: reads
  contexts:
  - place: customer-web::workspace::chat
permits:
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-member
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Support/ProposalOwnership.php
- kind: code
  role: implementation
  target: packages/Chat/src/Livewire/Chat/ChatInterface.php
---

# Only the requester reads this retained proposal — custom field creation proposal

Disclosure follows the requester’s personal Conversation and current workspace; workspace membership alone does not expose another person’s card.
