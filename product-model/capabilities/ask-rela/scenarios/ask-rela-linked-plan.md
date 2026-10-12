---
kind: primary
routes:
  main: Ask Rela for a linked plan
steps:
- text: Send the typed request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product reserves credits, retains the owned turn and calls the outbound language model
  kind: product
  entities:
  - entity: conversation
    effect: creates
    facts:
    - Title
    - Owner
    - Workspace
    - Purpose
    - Created At
    - Changed At
    to: Present
  - entity: message
    effect: creates
    facts:
    - Content
    - Author
    - Conversation
    - Created At
    - Processing Outcome
    to: Present
    with: conversation
  - entity: reply
    effect: creates
    facts:
    - Content
    - Conversation
    - Message
    - Response Outcome
    - Results
    to: Present
    with: conversation
  - entity: credit-balance
    effect: changes
    facts:
    - Remaining
    - Used
  - entity: company-creation-proposal
    effect: creates
    facts:
    - Proposed Name
    - Proposed Account Owner
    - Proposed Additional Values
    - Requester
    - Workspace
    - Conversation
    - Turn
    - Valid Until
    - Decision
    - Decision Time
    - Dependencies
    - Results
    to: Proposed
    with: conversation
  - entity: person-creation-proposal
    effect: creates
    facts:
    - Proposed Name
    - Proposed Company
    - Proposed Additional Values
    - Requester
    - Workspace
    - Conversation
    - Turn
    - Valid Until
    - Decision
    - Decision Time
    - Dependencies
    - Results
    to: Proposed
    with: conversation
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Http/Controllers/ChatController.php
- kind: code
  role: implementation
  target: packages/Chat/src/Actions/CreateConversation.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/CreditService.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/ProposalPlanService.php
---

# Ask Rela for a linked plan

## Trigger

The person sends a nonempty typed message of at most 5,000 characters, with an available model and credits.

## Outcome

The message and response are retained in the created or reused personal Chat. Related write proposals retain explicit dependencies and are presented as one plan; no proposed CRM write has run. Invitation sends stay separately approved. Credits follow reserved, idempotent settlement. Existing empty Chats are reused; first-send retention is part of this ability.
