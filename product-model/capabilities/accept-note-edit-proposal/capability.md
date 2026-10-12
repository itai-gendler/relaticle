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

# Accept note edit proposal

Decide the retained note edit proposal from its personal Chat. Acceptance rechecks the actual target operation and resolves approved dependencies at decision time; batches resolve per item.
