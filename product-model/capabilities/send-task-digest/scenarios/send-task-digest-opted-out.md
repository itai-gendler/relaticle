---
kind: validation
routes:
  main: Opted out
steps:
- text: "The Account\u2019s assigned work Digest Email preference is off."
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

# Opted out

## Trigger

The Account’s Task Digest Email preference is off.

## Outcome

No digest is sent for the opted-out Account. No exactly-once-per-day guarantee is asserted.
