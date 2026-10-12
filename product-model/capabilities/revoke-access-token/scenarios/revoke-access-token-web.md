---
kind: primary
routes:
  main: Revoke personal token
steps:
- text: Confirm token revocation
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
- text: The Product removes the owned credential
  kind: product
  entities:
  - entity: access-token
    effect: removes
    from: Present
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

# Revoke personal token

## Trigger

The Account confirms revocation of its token.

## Outcome

The token is removed and cannot authenticate later requests.
