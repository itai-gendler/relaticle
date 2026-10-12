---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: app/Actions/User/UpdateNotificationPreferences.php
- kind: code
  role: implementation
  target: app/Services/Notifications/DigestService.php
---

# Change notification settings

Change task-assignment in-app, task-assignment email and task-digest email preferences.
