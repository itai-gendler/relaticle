---
kind: primary
routes:
  board: Tasks board
steps:
- text: Move the selected card to another column and choose its position
  kind: actor
  actor: workspace-member
  entities: []
  contexts:
    board:
      place: customer-web::workspace::tasks
- text: The Product saves the Task column value and order together
  kind: product
  actor: workspace-member
  entities:
  - entity: task
    effect: changes
    facts:
    - Status
    - Order
    - Changed At
  contexts:
    board:
      place: customer-web::workspace::tasks
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/TaskResource/Pages/TasksBoard.php#moveCard
- kind: code
  role: implementation
  target: app/Policies/TaskPolicy.php#update
---

# Edit Task Status and Order on the board

## Trigger

The person moves an existing Task card to a configured Status column and chooses its position on the Tasks board.

## Outcome

Status is set to the resolved destination option and Order to the calculated position within one transaction. The successful movement is reported. The record’s links and assignments remain unchanged. Reordering within the current column preserves its selected Status.
