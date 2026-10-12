---
appliesTo:
- type: entity
  id: access-token
  effect: creates
- type: entity
  id: access-token
  effect: changes
  facts:
  - Read Grant
  - Create Grant
  - Update Grant
  - Delete Grant
references:
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/CreateAccessToken.php
- kind: code
  role: implementation
  target: app/Livewire/App/AccessTokens/ManageAccessTokens.php
---

# Token grants clamp to present authority and raw reveal occurs once

Personal token names are unique per Account; binding uses owned/joined workspaces and cannot change later. Creation and permission edits intersect requested grants with present workspace authority. Expiry choices are one, seven, 30, 60, 90, 180 and 365 days or never; default 180 days. The verifier is retained and the raw creation secret revealed once.
