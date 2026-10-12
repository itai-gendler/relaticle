---
appliesTo:
- type: entity
  id: workspace
  facts:
  - Scheduled Deletion
  - Personal Workspace
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/ScheduleWorkspaceDeletion.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CancelWorkspaceDeletion.php
- kind: code
  role: implementation
  target: app/Actions/Billing/CancelWorkspaceSubscription.php
---

# Deletion scheduling keeps grace and does not promise payment reversal

Personal Workspace scheduling is refused. Scheduling saves the configured default-30-day deadline and removes invitations transactionally before subscription cancellation is attempted. Caught provider failure preserves the schedule. Cancelling clears it and notifies the owner without establishing subscription restart. Eventual purge is a separate lifecycle.
