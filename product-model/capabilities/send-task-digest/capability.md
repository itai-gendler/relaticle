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

# Send Task digest

Attempt eligible Accounts’ scheduled local-08:00 task digests using assignment, activity, preference and due-date selection.
