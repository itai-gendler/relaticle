---
appliesTo:
- type: entity
  id: opportunity-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: company-edit-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: record-deletion-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: company-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: note-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: custom-field-options-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: custom-field-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: task-edit-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: opportunity-edit-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: custom-field-deletion-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: note-edit-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: person-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: task-creation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: custom-field-edit-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: workspace-invitation-proposal
  facts:
  - Decision
  - Results
- type: entity
  id: person-edit-proposal
  facts:
  - Decision
  - Results
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Batch and plan decisions preserve earlier successes

Whole-batch approve is refused: Batch proposals resolve per item via approveItem()/rejectItem(), not approve(). Items commit in separate transactions with retained outcomes. Plan approval is ordered; earlier accepted steps survive a later failure. Dismissing pending dependencies never undoes accepted CRM work.
