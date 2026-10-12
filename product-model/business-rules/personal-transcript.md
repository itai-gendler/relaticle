---
appliesTo:
- type: entity
  id: conversation
  effect: reads
- type: entity
  id: message
  effect: reads
- type: entity
  id: reply
  effect: reads
- type: entity
  id: opportunity-creation-proposal
  effect: reads
- type: entity
  id: company-edit-proposal
  effect: reads
- type: entity
  id: record-deletion-proposal
  effect: reads
- type: entity
  id: company-creation-proposal
  effect: reads
- type: entity
  id: note-creation-proposal
  effect: reads
- type: entity
  id: custom-field-options-proposal
  effect: reads
- type: entity
  id: custom-field-creation-proposal
  effect: reads
- type: entity
  id: task-edit-proposal
  effect: reads
- type: entity
  id: opportunity-edit-proposal
  effect: reads
- type: entity
  id: custom-field-deletion-proposal
  effect: reads
- type: entity
  id: note-edit-proposal
  effect: reads
- type: entity
  id: person-creation-proposal
  effect: reads
- type: entity
  id: task-creation-proposal
  effect: reads
- type: entity
  id: custom-field-edit-proposal
  effect: reads
- type: entity
  id: workspace-invitation-proposal
  effect: reads
- type: entity
  id: person-edit-proposal
  effect: reads
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationsQuery.php
- kind: code
  role: implementation
  target: packages/Chat/src/Queries/ConversationMessagesQuery.php
- kind: code
  role: implementation
  target: packages/Chat/src/Livewire/Chat/ChatInterface.php
---

# Transcript and card disclosure follows requester and Workspace

Personal Conversation queries, typed/synthetic transcript presentation and card lookups use the owning Account and current Workspace. Proposal workspace ownership alone does not expose another Account’s card. Accepted CRM targets retain their own workspace reading policy.
