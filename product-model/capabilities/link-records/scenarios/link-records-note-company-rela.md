---
kind: primary
routes:
  main: Link records — note-company rela
steps:
- text: Choose the relationship entries to link
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

# Link records — note-company rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired Companies changes without changing the target.
