---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/CreateAccessToken.php
domain: access-tokens
---

# Create an access token

Create a personal token with an authorized bound Workspace, expiry and clamped grants; reveal its raw secret once.
