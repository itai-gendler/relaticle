---
kind: primary
routes:
  main: Change notification preferences
steps:
- text: Save notification selections
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::notifications
  actor: workspace-viewer
- text: The Product retains owned assigned work notification preferences
  kind: product
  entities:
  - entity: account
    effect: changes
    facts:
    - Task Assignment In-app
    - Task Assignment Email
    - Task Digest Email
  contexts:
    main:
      place: customer-web::workspace::notifications
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/User/UpdateNotificationPreferences.php
---

# Change notification preferences

## Trigger

The Account changes its task notification selections.

## Outcome

Task Assignment In-app, Task Assignment Email and Task Digest Email selections are retained. Defaults are in-app assignment on, assignment email off and digest email on.
