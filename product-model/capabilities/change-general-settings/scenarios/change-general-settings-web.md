---
kind: primary
routes:
  main: Change General settings
steps:
- text: Save the working scope identity settings
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
- text: The Product saves the supplied General settings
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Name
    - Handle
    - Logo
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/EditWorkspace.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/UpdateWorkspaceName.php
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/UpdateWorkspaceLogo.php
---

# Change General settings

## Trigger

The owner supplies a changed Name, Handle or Logo.

## Outcome

The valid supplied General identity information is retained for the workspace.
