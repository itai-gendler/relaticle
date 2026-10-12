---
kind: primary
routes:
  main: Browse personal access tokens
steps:
- text: Open owned credentials
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
- text: The Product returns owned token information
  kind: product
  entities:
  - entity: access-token
    effect: reads
    facts:
    - Name
    - Workspace
    - Read Grant
    - Create Grant
    - Update Grant
    - Delete Grant
    - Created At
    - Expires At
    - Last Used At
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

# Browse personal access tokens

## Trigger

The Account opens its token settings.

## Outcome

Its personal token name, bound workspace, grants, creation/expiry/use times are available; retained credential verifiers and prior raw secrets are not disclosed.
