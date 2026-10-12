---
kind: primary
routes:
  main: Link records — task-person rela
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
  - entity: task-edit-proposal
    effect: creates
    facts:
    - Targets
    - Earlier Task Values
    - Proposed Task Values
    - Proposed Assignees
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
  target: app/Actions/Task/UpdateTask.php
---

# Link records — task-person rela

## Trigger

The actor supplies a relationship change.

## Outcome

An edit proposal retains the desired People changes without changing the target.
