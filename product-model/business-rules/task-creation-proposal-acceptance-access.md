---
appliesTo:
- type: entity
  id: task-creation-proposal
  effect: changes
  facts:
  - Results
  contexts:
  - place: customer-web::workspace::chat
permits:
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-owner
  when:
  - state: Proposed
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - state: Proposed
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - state: Proposed
- related:
  - verb: requests
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - state: Proposed
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

# Only the requester accepts a resolvable proposal or its items — task creation proposal

The requester decides a still-pending, unexpired personal proposal in its workspace. Target existence, current authority, references and definition constraints are rechecked before the target operation. Batch approval resolves individual items, not an atomic whole batch.

Per-item acceptance retains Results while the enclosing batch remains Proposed; the final decision retains the terminal status. Each item invokes the same decision-time target checks.
