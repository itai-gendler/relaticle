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

# Edit access-token permissions

Change a personal token’s grants, clamped to current authority, without changing its bound Workspace.
