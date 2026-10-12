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

# Expire proposals

Close pending proposals whose validity deadlines have elapsed on the Product’s expiry schedule.
