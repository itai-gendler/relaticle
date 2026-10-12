---
availability:
- place: customer-web::workspace
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Billing.php
- kind: code
  role: implementation
  target: app/Services/Billing/HostedWorkspaceAccess.php
---

# Browse billing information

Read published plan, trial, derived access status and AI credits, including paused-workspace self-service information.
