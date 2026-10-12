---
appliesTo:
- type: entity
  id: person-creation-proposal
  effect: changes
  facts:
  - Decision
  - Decision Time
  - Results
  to: Dismissed
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

# Only the requester dismisses this proposal — person creation proposal

The requester closes its still-resolvable personal proposal and pending dependents, without reversing committed target changes.
