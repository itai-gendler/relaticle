---
entities:
- entity: account
  shows:
  - Task Assignment In-app
  - Task Assignment Email
  - Task Digest Email
  collects:
  - Task Assignment In-app
  - Task Assignment Email
  - Task Digest Email
references:
- kind: code
  role: implementation
  target: app/Livewire/App/Notifications/ManageNotificationPreferences.php
---

# Notifications

The Account’s task notification preferences.
