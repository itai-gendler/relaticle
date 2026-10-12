---
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Models/AgentConversationMessage.php
domain: chats
---

# Reply

The retained answer and results of a response in a personal Chat. Rela calls an outbound model for this answer.

## Information kept

- **Content** — The retained content.
- **Conversation** — The retained conversation.
- **Message** — The retained message.
- **Response Outcome** — The retained response outcome.
- **Results** — The retained observable results, including per-item successes and failures where present.

## States

### Present

The reply is present.
