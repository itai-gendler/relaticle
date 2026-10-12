---
appliesTo:
- type: entity
  id: account
  facts:
  - Timezone
  - Last Sign-in
  - Task Digest Email
- type: entity
  id: task
  facts:
  - Assignees
  - Due Date
  - Status
  - Creation Source
references:
- kind: code
  role: implementation
  target: app/Console/Commands/SendTaskDigestCommand.php
- kind: code
  role: implementation
  target: app/Services/Notifications/DigestService.php
---

# Digest recipients and Tasks follow local time and preference selection

The schedule selects local 08:00 Accounts with sign-in within 30 days, enabled Task Digest Email and a nonempty payload. Across owned/joined workspaces it includes assigned nondeleted nonsample Tasks with Due Date before a cutoff computed by adding 24 hours to local day start after conversion to UTC, splitting overdue from today at local day start. Done is excluded when its option exists. Configured email is attempted; no exactly-once-per-day guarantee is asserted.

The cutoff is a fixed UTC day after the local-start instant, so it is not necessarily the next local midnight on a daylight-saving transition. Home preview severity separately computes both local-midnight boundaries before UTC conversion.
