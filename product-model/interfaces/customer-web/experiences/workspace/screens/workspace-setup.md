---
entities:
- entity: workspace
  shows:
  - Use Case
  - Use Case Context
  - Setup Step
  - Other Use Case
  collects:
  - Use Case
  - Use Case Context
  - Setup Step
  - Other Use Case
- entity: workspace-invitation
  shows:
  - Email
  - Role
  collects:
  - Email
  - Role
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/SetupWorkspace.php
---

# Workspace setup

The inspected use-case and invitation completion process for one workspace.
