---
appliesTo:
- type: capability
  id: browse-records
- type: capability
  id: create-record
- type: capability
  id: accept-workspace-invitation
- type: capability
  id: browse-record-history
- type: capability
  id: browse-workspace-activity
- type: entity
  id: account
  facts:
  - Email Verified
references:
- kind: code
  role: implementation
  target: app/Policies/Concerns/ChecksWorkspaceCapability.php
- kind: code
  role: implementation
  target: app/Policies/OpportunityPolicy.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
- kind: code
  role: implementation
  target: app/Providers/Filament/AppPanelProvider.php
---

# Identity verification remains distinct from role authority

Customer panel verified middleware and the inspected list/create/bulk policies require verified email; shared CRM lists invoke viewAny. MCP activity invokes applicable record viewAny checks. Invitation acceptance has its verified identity gate. Ordinary selected-record view/update/delete/restore checks use workspace capability without universal email verification. Definition discovery does not inherit record policy by name. Identity and request validation are not new Actors.
