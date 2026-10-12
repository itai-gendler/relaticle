---
kind: primary
routes:
  main: Cancel workspace deletion
steps:
- text: Choose Cancel deletion
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
- text: The Product clears the retained deletion deadline
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Scheduled Deletion
    from: Scheduled for Deletion
    to: Active
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CancelWorkspaceDeletion.php
---

# Cancel workspace deletion

## Trigger

The workspace has a retained deletion schedule.

## Outcome

The deadline is cleared and the owner is notified; no subscription restart is asserted.
