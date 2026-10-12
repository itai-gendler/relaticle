---
kind: edge
routes:
  main: Task batch keeps per-item results
steps:
- text: Approve selected batch items
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product commits each successful item independently and retains item results
  kind: product
  entities:
  - entity: task
    effect: creates
    facts:
    - Title
    - Status
    - Priority
    - Due Date
    - Description
    - Assignees
    - Companies
    - People
    - Opportunities
    - Order
    - Additional Values
    - Workspace
    - Creator
    - Creation Source
    - Created At
    - Changed At
    to: Active
  - entity: task-creation-proposal
    effect: changes
    facts:
    - Results
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Services/PendingActionService.php
---

# Task batch keeps per-item results

## Trigger

One Task batch item succeeds and a later item fails.

## Outcome

The successful Task remains, item results show the failure, and pending items remain individually resolvable. Calling whole-batch approve is refused.
