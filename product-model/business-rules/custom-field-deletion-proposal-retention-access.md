---
appliesTo:
- type: entity
  id: custom-field-deletion-proposal
  effect: creates
  to: Proposed
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

# The requesting workspace writer may retain this proposal — custom field deletion proposal

Retention checks the actual underlying create/update/delete, field-management or invitation authority and same-workspace references before keeping a personal Proposed draft.
