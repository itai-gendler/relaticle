---
appliesTo:
- type: entity
  id: opportunity-creation-proposal
  effect: creates
- type: entity
  id: company-edit-proposal
  effect: creates
- type: entity
  id: record-deletion-proposal
  effect: creates
- type: entity
  id: company-creation-proposal
  effect: creates
- type: entity
  id: note-creation-proposal
  effect: creates
- type: entity
  id: custom-field-options-proposal
  effect: creates
- type: entity
  id: custom-field-creation-proposal
  effect: creates
- type: entity
  id: task-edit-proposal
  effect: creates
- type: entity
  id: opportunity-edit-proposal
  effect: creates
- type: entity
  id: custom-field-deletion-proposal
  effect: creates
- type: entity
  id: note-edit-proposal
  effect: creates
- type: entity
  id: person-creation-proposal
  effect: creates
- type: entity
  id: task-creation-proposal
  effect: creates
- type: entity
  id: custom-field-edit-proposal
  effect: creates
- type: entity
  id: workspace-invitation-proposal
  effect: creates
- type: entity
  id: person-edit-proposal
  effect: creates
- type: capability
  id: create-record
- type: capability
  id: edit-record
- type: capability
  id: delete-record
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteCreateTool.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteUpdateTool.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteDeleteTool.php
---

# Retaining a proposal performs no target write

Rela write tools retain Proposed information and dependencies. CRM records, field definitions/options and invitations change only at the separately accepted target operation; editing a creation card changes the proposal.
