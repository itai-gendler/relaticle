---
kind: primary
routes:
  main: Delete personal Chat
steps:
- text: Confirm deletion of the owned transcript
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product removes the selected transcript and its dependent retained information
  kind: product
  entities:
  - entity: conversation
    effect: removes
    from: Present
  - entity: message
    effect: removes
    from: Present
    with: conversation
  - entity: reply
    effect: removes
    from: Present
    with: conversation
  - entity: opportunity-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: company-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: record-deletion-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: company-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: note-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: custom-field-options-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: custom-field-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: task-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: opportunity-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: custom-field-deletion-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: note-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: person-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: task-creation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: custom-field-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: workspace-invitation-proposal
    effect: removes
    from: Proposed
    with: conversation
  - entity: person-edit-proposal
    effect: removes
    from: Proposed
    with: conversation
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Actions/DeleteConversation.php
---

# Delete personal Chat

## Trigger

The Account confirms deletion of a personal conversation.

## Outcome

The conversation, transcript and retained proposals are removed; CRM records already accepted from it remain.
