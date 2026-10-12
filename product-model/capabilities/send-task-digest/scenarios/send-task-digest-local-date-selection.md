---
kind: primary
routes:
  main: Local date selection
steps:
- text: "The Account\u2019s local-date boundary differs from UTC and assigned work span its working scopes."
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

# Local date selection

## Trigger

The Account’s local-date boundary differs from UTC and assigned Tasks span its workspaces.

## Outcome

The digest selects overdue and Tasks in the implemented 24-hour cutoff window across the Account’s workspaces, using local midnight converted to UTC; it excludes samples and Done Tasks when that option exists. No exactly-once-per-day guarantee is asserted.


## Edge cases

- On a daylight-saving transition the fixed 24-hour cutoff can differ from the next local midnight. The implemented cutoff remains the source behavior.
