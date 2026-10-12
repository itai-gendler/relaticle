---
appliesTo:
- type: entity
  id: credit-balance
  effect: changes
  facts:
  - Remaining
  - Used
- type: capability
  id: ask-rela
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/CreditService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Jobs/ProcessChatMessage.php
---

# Response credit reserve and resolution are idempotent

Credits are reserved atomically before dispatch; exhausted reservation returns 402. Successful generation settles actual usage and inspected failure paths refund reserved usage idempotently. Stopping visible streaming does not imply aborting the provider or zero charge. A hosted-access recheck can fail and refund during processing.
