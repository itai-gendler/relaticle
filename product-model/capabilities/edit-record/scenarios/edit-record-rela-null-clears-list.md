---
kind: primary
routes:
  main: Rela null list becomes a clear
steps:
- text: Request an explicit list clear
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product normalizes the supplied null list and retains an edit proposal
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
  target: packages/Chat/src/Tools/Task/UpdateTaskTool.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseWriteUpdateTool.php
---

# Rela null list becomes a clear

## Trigger

A Rela Task edit explicitly supplies a null relationship list.

## Outcome

The normalized proposed list is empty; acceptance will clear that supplied list while preserving omitted lists.
