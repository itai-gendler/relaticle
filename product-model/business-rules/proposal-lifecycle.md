---
appliesTo:
- type: entity
  id: opportunity-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: company-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: record-deletion-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: company-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: note-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: custom-field-options-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: custom-field-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: task-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: opportunity-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: custom-field-deletion-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: note-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: person-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: task-creation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: custom-field-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: workspace-invitation-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
- type: entity
  id: person-edit-proposal
  facts:
  - Decision
  - Decision Time
  - Valid Until
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/config/chat.php
---

# Pending proposals expire or supersede without replaying writes

Configured lifetime is 1,440 minutes ordinarily and 10,080 minutes in a setup Chat. Due pending proposals expire; later turns supersede pending earlier proposals. Decided or expired proposals cannot write again. Resolved/superseded context conveys status without rewriting earlier tool results. Target changes do not establish an automatic Outdated state.
