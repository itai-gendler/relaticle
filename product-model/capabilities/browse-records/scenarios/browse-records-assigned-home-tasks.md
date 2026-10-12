---
kind: primary
routes:
  home: Assigned Tasks on Home
steps:
- text: Open Home and its assigned-work preview
  kind: actor
  actor: workspace-viewer
  entities: []
  contexts:
    home:
      place: customer-web::workspace::home
- text: The Product returns at most five assigned Tasks and presents their titles
    and parsed due dates
  kind: product
  actor: workspace-viewer
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Due Date
    - Status
    - Assignees
    - Created At
    - Workspace
  contexts:
    home:
      place: customer-web::workspace::home
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/MyTasksService.php#forUser
- kind: code
  role: implementation
  target: app/Filament/Pages/Dashboard.php#myTasks
- kind: code
  role: implementation
  target: packages/Chat/resources/views/filament/pages/partials/my-tasks.blade.php
---

# Browse assigned Tasks on Home

## Trigger

The person opens Home in the selected workspace and has assigned Tasks.

## Outcome

Home presents at most five nondeleted assigned Tasks, with Title and the parsed Due Date when present. Done Tasks are excluded when that option exists. Selection orders earliest due datetime first, missing dates last, and newest creation as the fallback. Other collection facts and controls are not disclosed by this preview. Date severity uses the Account’s local-midnight boundaries before UTC conversion.

## Edge cases

- With no eligible assigned Tasks, the preview is empty.
- Without a Done option, the Done exclusion is not applied.
- The View all destination opens the Tasks collection with the assigned-to-me filter.
