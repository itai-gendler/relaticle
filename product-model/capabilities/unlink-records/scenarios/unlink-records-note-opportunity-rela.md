---
kind: primary
routes:
  main: Unlink records — note-opportunity rela
steps:
- text: Choose the relationship entries to unlink
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product retains the edit proposal
  kind: product
  entities:
  - entity: note-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Note Values
    - Proposed Note Values
    - Proposed Companies
    - Proposed People
    - Proposed Opportunities
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
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: app/Actions/Note/UpdateNote.php
---

# Unlink records — note-opportunity rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired Opportunities changes without changing the target.
