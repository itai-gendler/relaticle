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

# Stop a response

Stop the visible response stream; provider-call abortion and reversal of CRM work are not established.
