---
kind: validation
routes:
  main: Duplicate name
steps:
- text: Another token owned by this identity already has the requested name.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/CreateAccessToken.php
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
---

# Duplicate name

## Trigger

Another token owned by this Account already has the requested name.

## Outcome

Validation rejects the name without issuing a credential.
