---
kind: primary
routes:
  main: Expire due proposals
steps:
- text: The expiry schedule finds elapsed validity deadlines
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  unattended: true
- text: The Product expires the due pending proposals
  kind: product
  entities:
  - entity: opportunity-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: company-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: record-deletion-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: company-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: note-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: custom-field-options-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: custom-field-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: task-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: opportunity-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: custom-field-deletion-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: note-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: person-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: task-creation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: custom-field-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: workspace-invitation-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  - entity: person-edit-proposal
    effect: changes
    facts:
    - Decision
    - Decision Time
    from: Proposed
    to: Expired
  contexts:
    main:
      place: customer-web::workspace::chat
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Commands/ExpirePendingActionsCommand.php
- kind: code
  role: implementation
  target: packages/Chat/config/chat.php
---

# Expire due proposals

## Trigger

The Product’s expiry schedule reaches pending proposal deadlines.

## Outcome

Due pending proposals become Expired; no target writes are performed and resolved decisions remain.
