---
kind: primary
routes:
  main: Read personal Chats
steps:
- text: Open the owned Chat list and selected transcript
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the owned working scope transcripts
  kind: product
  entities:
  - entity: conversation
    effect: reads
    facts:
    - Title
    - Owner
    - Workspace
    - Purpose
    - Created At
    - Changed At
  - entity: message
    effect: reads
    facts:
    - Content
    - Author
    - Conversation
    - Created At
    - Processing Outcome
  - entity: reply
    effect: reads
    facts:
    - Content
    - Conversation
    - Message
    - Response Outcome
    - Results
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationsQuery.php
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationMessagesQuery.php
---

# Read personal Chats

## Trigger

The Account opens the workspace Chat list or a selected conversation.

## Outcome

Its own conversation titles and selected typed transcript are available; synthetic processing rows keep their inspected presentation distinctions.
