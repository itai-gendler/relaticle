---
entities:
- entity: access-token
  shows:
  - Name
  - Workspace
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
  - Expires At
  - Created At
  - Last Used At
  collects:
  - Name
  - Workspace
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
  - Expires At
references:
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
---

# Access tokens

Personal token information and input; the newly created raw secret is a one-time result on this process.
