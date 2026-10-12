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

# Ask Rela

Send a question or CRM request. First send creates or reuses the conversation, retains the typed message and starts an outbound model response. Suggested writes remain proposals awaiting decisions.
