---
kind: primary
routes:
  main: Edit opportunity creation proposal
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
  - entity: opportunity-creation-proposal
    effect: changes
    facts:
    - Proposed Name
    - Proposed Company
    - Proposed Point of Contact
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

# Edit opportunity creation proposal

## Trigger

An editable personal creation proposal is still pending and valid.

## Outcome

The chosen proposed core information and active configured values are retained on the proposal; the target is not created. Excluded fields are represented in later accepted results rather than falsely reported as written.
