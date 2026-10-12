---
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Models/AgentConversationMessage.php
domain: chats
---

# Message

A retained contribution to a personal Chat, including the observable processing or failure outcome.

## Information kept

- **Content** — The retained content.
- **Author** — The retained author.
- **Conversation** — The retained conversation.
- **Created At** — When this instance was created.
- **Processing Outcome** — The retained processing outcome.

## States

### Present

The message is present.
