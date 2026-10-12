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

# Delete a Chat

Remove a personal Chat and its transcript and proposals, preserving CRM records already written.
