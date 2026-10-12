---
kind: validation
routes:
  main: Noncreation proposal editor refused
steps:
- text: The selected proposal is an edit, deletion, field or invitation proposal.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalEditor.php
---

# Noncreation proposal editor refused

## Trigger

The selected proposal is an edit, deletion, field or invitation proposal.

## Outcome

The creation editor does not change that proposal.
