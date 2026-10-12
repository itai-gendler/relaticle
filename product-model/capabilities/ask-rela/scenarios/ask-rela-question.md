---
kind: primary
routes:
  chat: Question in Chat
  home: Question from Home
steps:
- text: Send the typed request
  kind: actor
  entities: []
  contexts:
    chat:
      place: customer-web::workspace::chat
    home:
      place: customer-web::workspace::home
  actor: workspace-viewer
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
  contexts:
    chat:
      place: customer-web::workspace::chat
    home:
      place: customer-web::workspace::chat
  actor: workspace-viewer
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
- kind: code
  role: implementation
  target: packages/Chat/resources/views/filament/pages/dashboard.blade.php
- kind: code
  role: implementation
  target: packages/Chat/resources/js/chat/send.js
---

# Ask Rela a question

## Trigger

The person sends a nonempty typed message of at most 5,000 characters, with an available model and credits.

## Outcome

The message and response are retained in the created or reused personal Chat. The answer and any read results are visible. Credits follow reserved, idempotent settlement. Existing empty Chats are reused; first-send retention is part of this ability.


## Edge cases

- The Home composer carries the typed document into Chat before first-message delivery. If the bootstrap storage call fails, Home reports the error and no send occurs.
