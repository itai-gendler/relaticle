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

# Dismiss company creation proposal

Decide the retained company creation proposal from its personal Chat. Dismissal closes the proposal without reversing accepted target operations.
