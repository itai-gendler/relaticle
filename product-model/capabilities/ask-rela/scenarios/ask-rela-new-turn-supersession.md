---
kind: edge
routes:
  main: A later turn supersedes pending proposals
steps:
- text: Send the later typed request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the new message and supersedes pending earlier-turn proposals
  kind: product
  entities:
  - entity: message
    effect: creates
    facts:
    - Content
    - Author
    - Conversation
    - Created At
    - Processing Outcome
    to: Present
  - entity: opportunity-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: company-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: record-deletion-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: company-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: note-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: custom-field-options-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: custom-field-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: task-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: opportunity-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: custom-field-deletion-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: note-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: person-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: task-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: custom-field-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: workspace-invitation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  - entity: person-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Superseded
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
---

# A later turn supersedes pending proposals

## Trigger

A personal Chat has proposals from an earlier turn and the person sends a later request.

## Outcome

The later turn closes earlier pending proposals as Superseded; accepted decisions and their target changes remain.
