---
appliesTo:
- type: capability
  id: browse-records
- type: capability
  id: view-record
- type: capability
  id: create-record
- type: capability
  id: edit-record
- type: capability
  id: delete-record
- type: capability
  id: ask-rela
- type: capability
  id: browse-billing-information
- type: entity
  id: product-configuration
  facts:
  - Billing Enabled
references:
- kind: code
  role: implementation
  target: app/Enums/BillingStatus.php
- kind: code
  role: implementation
  target: app/Services/Billing/HostedWorkspaceAccess.php
- kind: code
  role: implementation
  target: app/Http/Middleware/EnsureHostedWorkspaceAccess.php
---

# Hosted access follows derived billing eligibility

Billing Enabled off permits hosted access. When on, precedence is live Past due, valid subscription, Enterprise, generic Trial, grandfathered, ended subscription, ended trial, granted paid plan, then Free. Past due/subscribed/Enterprise/Trial/grandfathered/granted allow access; Free/ended statuses pause it. Guarded API/MCP/Chat paths return 402 and guarded web destinations redirect to Billing. General, profile, token and workspace self-service exceptions remain. Access and billing status are derived, not invented kept facts.
