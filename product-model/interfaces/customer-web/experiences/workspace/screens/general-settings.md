---
entities:
- entity: workspace
  shows:
  - Name
  - Handle
  - Logo
  - Scheduled Deletion
  collects:
  - Name
  - Handle
  - Logo
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/EditWorkspace.php
---

# General workspace settings

General identity settings and the current deletion schedule.
