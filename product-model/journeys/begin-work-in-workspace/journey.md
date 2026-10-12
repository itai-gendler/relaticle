---
actors:
- workspace-owner
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Filament/Pages/SetupWorkspace.php
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsInviteStep.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/CreateSetupConversation.php
---

# Begin work in a configured Workspace

## Goal

Create an owned Workspace and complete its required inspected setup.

## Success criterion

The same Account owns the created Workspace, has completed the required setup and reaches its configured Home or personal setup Chat.
