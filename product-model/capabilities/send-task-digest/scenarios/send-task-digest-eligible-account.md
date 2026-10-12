---
kind: primary
routes:
  main: Eligible account
steps:
- text: The schedule reaches local 08:00 for a recently active opted-in Account with assigned eligible assigned
    works.
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
- text: The Product evaluates the assigned work and attempts the configured digest
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

# Eligible account

## Trigger

The schedule reaches local 08:00 for a recently active opted-in Account with assigned eligible Tasks.

## Outcome

The configured email is attempted with grouped workspace Task information. No exactly-once-per-day guarantee is asserted.
