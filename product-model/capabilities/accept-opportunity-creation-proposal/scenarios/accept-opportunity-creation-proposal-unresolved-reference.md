---
kind: validation
routes:
  main: Unresolved plan reference
steps:
- text: The selected sale record creation depends on an earlier result that is absent, unresolved, foreign or lacks
    the requested batch item.
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
  target: packages/Chat/src/Services/PlanReferenceResolver.php
---

# Unresolved plan reference

## Trigger

The Opportunity creation depends on an earlier result that is absent, unresolved, foreign or lacks the requested batch item.

## Outcome

Reference resolution fails before the Opportunity target write; the still-pending proposal can retain the reported error.
