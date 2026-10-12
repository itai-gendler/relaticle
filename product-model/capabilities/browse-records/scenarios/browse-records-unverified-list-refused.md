---
kind: validation
routes:
  main: Unverified list identity
steps:
- text: "The acting identity\u2019s email is unverified."
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
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Policies/Concerns/ChecksWorkspaceCapability.php
---

# Unverified list identity

## Trigger

The acting Account’s email is unverified.

## Outcome

The shared list request is refused rather than returning a page. This case does not extend verification to ordinary selected-record reads.
