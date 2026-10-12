---
kind: edge
routes:
  main: Create token with clamped grants
steps:
- text: Supply the token name, working scope, expiry and grants
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::access-tokens
  actor: workspace-viewer
- text: The Product stores the bound credential and reveals its creation secret once
  kind: product
  entities:
  - entity: access-token
    effect: creates
    facts:
    - Name
    - Owner
    - Workspace
    - Read Grant
    - Create Grant
    - Update Grant
    - Delete Grant
    - Created At
    - Expires At
    - Last Used At
    - Credential Verifier
    to: Present
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

# Create token with clamped grants

## Trigger

The Account supplies a unique personal token name, an owned or joined workspace, expiry and requested grants.

## Outcome

The workspace-bound token is retained with a stored verifier and grants intersected with current role authority. Its raw secret is revealed once on creation. Expiry choices are one, seven, 30, 60, 90, 180 or 365 days or no expiry; default is 180 days.
