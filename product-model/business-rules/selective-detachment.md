---
appliesTo:
- type: capability
  id: unlink-records
- type: capability
  id: unassign-member
references:
- kind: code
  role: implementation
  target: app/Actions/Task/DetachTaskRelationships.php
---

# Detachment removes only specified entries

Dedicated link and assignment detachment removes only named entries, preserving other links and linked records. An existing former-member assignment can be removed without new-assignee membership validation.
