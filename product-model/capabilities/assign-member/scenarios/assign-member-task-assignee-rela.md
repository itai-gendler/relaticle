---
kind: primary
routes:
  main: "Assign member \u2014 task-assignee rela"
steps:
- text: Choose the identity assignment change
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

# Assign member — task-assignee rela

## Trigger

The actor supplies an assignment change.

## Outcome

The assignment change is retained in an edit proposal; the record remains unchanged.
