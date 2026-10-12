---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Http/Controllers/ChatController.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
domain: chats
---

# Edit a creation proposal

Change a retained CRM creation proposal’s editable information before its decision.
