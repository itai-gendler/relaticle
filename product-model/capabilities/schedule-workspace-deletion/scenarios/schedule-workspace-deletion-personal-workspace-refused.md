---
kind: validation
routes:
  main: Personal workspace deletion refusal
steps:
- text: The selected scope has its Personal Workspace flag set.
  kind: condition
  actor: workspace-owner
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Personal Workspace
  contexts:
    main:
      place: customer-web::workspace::general-settings
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/ScheduleWorkspaceDeletion.php
---

# Personal workspace deletion refusal

## Trigger

The selected workspace is personal.

## Outcome

Direct deletion scheduling is refused and the workspace remains Active.
