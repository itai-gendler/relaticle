---
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Models/AgentConversation.php
relations:
- entity: message
  verb: contains
  cardinality: one-to-many
- entity: reply
  verb: contains
  cardinality: one-to-many
- entity: company-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: person-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: opportunity-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: task-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: note-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: company-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: person-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: opportunity-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: task-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: note-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: record-deletion-proposal
  verb: contains
  cardinality: one-to-many
- entity: custom-field-creation-proposal
  verb: contains
  cardinality: one-to-many
- entity: custom-field-edit-proposal
  verb: contains
  cardinality: one-to-many
- entity: custom-field-options-proposal
  verb: contains
  cardinality: one-to-many
- entity: custom-field-deletion-proposal
  verb: contains
  cardinality: one-to-many
- entity: workspace-invitation-proposal
  verb: contains
  cardinality: one-to-many
domain: chats
---

# Conversation

A personal workspace Chat, retained for its owning Account with its typed messages, replies and proposals.

## Information kept

- **Title** — The retained title.
- **Owner** — The retained owner.
- **Workspace** — The workspace to which this instance belongs.
- **Purpose** — The retained purpose.
- **Created At** — When this instance was created.
- **Changed At** — When this instance was last changed.

## States

### Present

The conversation is present.
