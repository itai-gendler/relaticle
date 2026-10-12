---
kind: primary
routes:
  main: Schedule workspace deletion
steps:
- text: Confirm the deletion schedule
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
- text: The Product saves the grace deadline, removes invitations and attempts cancellation
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Scheduled Deletion
    from: Active
    to: Scheduled for Deletion
  - entity: workspace-invitation
    effect: removes
    from: Issued
  contexts:
    main:
      place: customer-web::workspace::general-settings
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/ScheduleWorkspaceDeletion.php
- kind: code
  role: implementation
  target: app/Actions/Billing/CancelWorkspaceSubscription.php
---

# Schedule workspace deletion

## Trigger

A nonpersonal workspace has no pending deletion schedule.

## Outcome

The configured deadline, default 30 days ahead, is retained and pending invitations are removed. Subscription cancellation is attempted afterward; its caught provider failure does not undo the schedule. The owner is notified.
