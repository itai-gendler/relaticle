---
kind: primary
routes:
  main: Switch workspace
steps:
- text: Select the working scope
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
- text: The Product persists the selected working scope
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Current Workspace
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Models/Concerns/HasWorkspaces.php
- kind: code
  role: implementation
  target: app/Listeners/SwitchWorkspace.php
---

# Switch workspace

## Trigger

The Account selects another of its workspaces.

## Outcome

The web selection is persisted and the selected workspace becomes the current customer context.
