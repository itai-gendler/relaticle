---
appliesTo:
- type: entity
  id: task-creation-proposal
  effect: changes
  facts:
  - Proposed Title
  - Proposed Assignees
  - Proposed Companies
  - Proposed People
  - Proposed Opportunities
  - Proposed Additional Values
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
  target: packages/Chat/src/Services/ProposalEditor.php
---

# Only the requester edits a pending creation proposal

The requester’s still-pending, unexpired creation proposal is editable for the inspected core fields and active configured values. Other proposal shapes receive no editor grant.
