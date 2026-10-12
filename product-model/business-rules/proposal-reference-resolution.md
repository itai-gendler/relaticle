---
appliesTo:
- type: entity
  id: opportunity-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: company-edit-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: record-deletion-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: company-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: note-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: custom-field-options-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: custom-field-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: task-edit-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: opportunity-edit-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: custom-field-deletion-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: note-edit-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: person-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: task-creation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: custom-field-edit-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: workspace-invitation-proposal
  facts:
  - Dependencies
  - Results
- type: entity
  id: person-edit-proposal
  facts:
  - Dependencies
  - Results
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PlanReferenceResolver.php
- kind: code
  role: implementation
  target: packages/Chat/src/Support/RecordNameResolver.php
---

# References resolve from accepted earlier results at decision time

Dependencies resolve only at acceptance from an accepted earlier same-workspace result and requested batch item. Missing, unresolved or foreign results fail before target writes. Cards display linked proposed names and their step numbers.
