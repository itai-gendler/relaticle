---
appliesTo:
- type: entity
  id: workspace-invitation-proposal
  effect: changes
  facts:
  - Decision
  - Decision Time
  - Results
  to: Accepted
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

# Only the requester accepts a resolvable proposal — workspace invitation proposal

The requester decides a still-pending, unexpired personal proposal in its workspace. Target existence, current authority, references and definition constraints are rechecked before the target operation. Batch approval resolves individual items, not an atomic whole batch.
