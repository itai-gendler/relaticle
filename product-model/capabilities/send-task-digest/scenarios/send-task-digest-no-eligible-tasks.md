---
kind: validation
routes:
  main: No eligible tasks
steps:
- text: The eligible Account has no assigned open nonsample work in the due-date window.
  kind: condition
  entities:
  - entity: account
    effect: reads
    facts:
    - Timezone
    - Last Sign-in
    - Task Digest Email
  contexts:
    main:
      place: customer-web::workspace::notifications
  unattended: true
- text: The Product evaluates the assigned work and skips sending
  kind: product
  entities:
  - entity: task
    effect: reads
    facts:
    - Title
    - Status
    - Due Date
    - Assignees
    - Creation Source
    - Workspace
  contexts:
    main:
      place: customer-web::workspace::notifications
references:
- kind: code
  role: implementation
  target: app/Services/Notifications/DigestService.php
- kind: code
  role: implementation
  target: app/Console/Commands/SendTaskDigestCommand.php
---

# No eligible tasks

## Trigger

The eligible Account has no assigned open nonsample Tasks in the due-date window.

## Outcome

No empty digest is sent. No exactly-once-per-day guarantee is asserted.
