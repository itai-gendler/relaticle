---
kind: edge
routes:
  main: Edit token grants with clamping
steps:
- text: Save the requested grants
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
- text: The Product retains the clamped grant selection
  kind: product
  entities:
  - entity: access-token
    effect: changes
    facts:
    - Read Grant
    - Create Grant
    - Update Grant
    - Delete Grant
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

# Edit token grants with clamping

## Trigger

The Account changes requested grants on its own token.

## Outcome

The grants are intersected with current authority for the bound workspace; disallowed grants are removed and the workspace binding remains unchanged.
