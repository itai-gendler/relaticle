---
appliesTo:
- type: entity
  id: opportunity-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: company-edit-proposal
  effect: changes
  to: Accepted
- type: entity
  id: record-deletion-proposal
  effect: changes
  to: Accepted
- type: entity
  id: company-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: note-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: custom-field-options-proposal
  effect: changes
  to: Accepted
- type: entity
  id: custom-field-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: task-edit-proposal
  effect: changes
  to: Accepted
- type: entity
  id: opportunity-edit-proposal
  effect: changes
  to: Accepted
- type: entity
  id: custom-field-deletion-proposal
  effect: changes
  to: Accepted
- type: entity
  id: note-edit-proposal
  effect: changes
  to: Accepted
- type: entity
  id: person-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: task-creation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: custom-field-edit-proposal
  effect: changes
  to: Accepted
- type: entity
  id: workspace-invitation-proposal
  effect: changes
  to: Accepted
- type: entity
  id: person-edit-proposal
  effect: changes
  to: Accepted
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: app/Actions/CustomFields/UpdateCustomField.php
---

# Acceptance rechecks the current target operation

The service locks a still-resolvable proposal, binds its workspace and invokes the allowed target action as the deciding person. Target existence, current authority, workspace references and definition constraints are rechecked. Proposal creation is not an authorization snapshot.
