---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
domain: chats
---

# Dismiss custom field options proposal

Decide the retained custom field options proposal from its personal Chat. Dismissal closes the proposal without reversing accepted target operations.
