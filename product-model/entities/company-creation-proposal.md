---
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Models/PendingAction.php
domain: chats
---

# Company Creation Proposal

A retained Company Creation Proposal in a personal Chat. Its proposed information, requester, deadline, dependencies and results are distinct from the target’s kept information.

## Information kept

- **Proposed Name** — The proposed name.
- **Proposed Account Owner** — The proposed account owner.
- **Proposed Additional Values** — The proposed additional values.
- **Requester** — The Account for whom the proposal was retained.
- **Workspace** — The workspace to which this instance belongs.
- **Conversation** — The retained conversation.
- **Turn** — The response turn grouping a proposal plan.
- **Valid Until** — The proposal’s expiry deadline.
- **Decision** — The retained resolution status, including partial item outcomes.
- **Decision Time** — When a decision was retained.
- **Dependencies** — References to earlier proposed steps, resolved from accepted results at decision time.
- **Results** — The retained observable results, including per-item successes and failures where present.

## States

### Proposed

The proposal awaits a decision and performs no target write.

### Accepted

The accepted operation results and decision are retained.

### Dismissed

The proposal is dismissed without reversing previously accepted target changes.

### Expired

The proposal’s validity deadline has closed its pending decision.

### Superseded

A later turn has closed the pending proposal.
