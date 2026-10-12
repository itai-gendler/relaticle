---
kind: primary
routes:
  main: Edit note creation proposal
steps:
- text: Edit the proposed creation information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product saves the editable proposed information
  kind: product
  entities:
  - entity: note-creation-proposal
    effect: changes
    facts:
    - Proposed Title
    - Proposed Companies
    - Proposed People
    - Proposed Opportunities
    - Proposed Additional Values
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalEditor.php
---

# Edit note creation proposal

## Trigger

An editable personal creation proposal is still pending and valid.

## Outcome

The chosen proposed core information and active configured values are retained on the proposal; the target is not created. Excluded fields are represented in later accepted results rather than falsely reported as written.
