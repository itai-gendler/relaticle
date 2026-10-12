---
kind: validation
routes:
  main: Foreign workspace
steps:
- text: "The chosen working scope is outside the identity\u2019s owned and joined working scopes."
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

# Foreign workspace

## Trigger

The chosen workspace is outside the Account’s owned and joined workspaces.

## Outcome

Creation is refused without binding a token to that workspace.
