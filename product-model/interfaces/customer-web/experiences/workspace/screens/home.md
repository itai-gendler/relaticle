---
entities:
- entity: account
  shows:
  - Name
- entity: task
  shows:
  - Title
  - Due Date
  collects:
  - Title
  - Status
  - Priority
  - Due Date
  - Description
  - Assignees
  - Companies
  - People
  - Opportunities
  - Additional Values
- entity: workspace-invitation
  shows:
  - Email
  - Role
  - Workspace
  - Expires At
- entity: conversation
  shows:
  - Title
- entity: message
  collects:
  - Content
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Dashboard.php
- kind: code
  role: implementation
  target: packages/Chat/src/Services/MyTasksService.php
- kind: code
  role: implementation
  target: packages/Chat/resources/views/filament/pages/partials/my-tasks.blade.php
---

# Home

Assigned work, current incoming invitations and recent personal Chats.
