---
entities:
- entity: account
  shows:
  - Name
- entity: workspace
  shows:
  - Name
  - Handle
  - Logo
  - Referral Source
  - Referral Detail
  - Referral Prompt
  collects:
  - Name
  - Handle
  - Logo
  - Referral Source
  - Referral Detail
  - Referral Prompt
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/CreateWorkspace.php
---

# Create workspace

The process of creating an owned workspace and handing off to its required setup.
