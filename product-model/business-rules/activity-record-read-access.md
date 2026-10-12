---
appliesTo:
- type: entity
  id: activity
  effect: reads
  contexts:
  - place: customer-web::workspace::chat
  - place: customer-web::workspace::company
  - place: customer-web::workspace::person
  - place: customer-web::workspace::opportunity
  - place: customer-web::workspace::task
  - place: customer-web::workspace::note
  - place: agent-access::company
  - place: agent-access::person
  - place: agent-access::opportunity
  - place: agent-access::task
  - place: agent-access::note
permits:
- related:
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when: &id001
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  - verb: connects
    entity: ai-agent
  when: *id001
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when: &id002
  - entity: membership
    fact: Role
    is: Member
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  - verb: connects
    entity: ai-agent
  when: *id002
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when: &id003
  - entity: membership
    fact: Role
    is: Viewer
- related:
  - verb: contains
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  - verb: connects
    entity: ai-agent
  when: *id003
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
- kind: code
  role: implementation
  target: app/Policies/OpportunityPolicy.php#view
- kind: code
  role: implementation
  target: app/Mcp/Tools/Concerns/ChecksTokenAbility.php#denyIfTokenCannot
---

# Workspace members may read visible-subject history

For a selected-record history query, the selected CRM subject must exist, be visible to the acting person and belong to the query workspace. A missing or soft-deleted selected subject is not returned.

For cross-record Chat reads, no selected-subject precondition applies. The existing workspace-related grants remain applicable, while the separate requested-query authorization Rule requires Activity View. These grants alone do not authorize a cross-record query. Every returned Activity remains bounded to the query workspace.

On REST token-bearing requests the actual selected credential must hold the corresponding read/create/update/delete ability; Passport cookie credentials are refused. On MCP OAuth the selected credential must hold mcp:use, while personal tokens require the operation ability. Session-only REST calls follow their inspected policy path. Ownership of some other credential never qualifies the request.

For MCP activity reads, the actual current persisted personal token must hold read; a Passport access token must hold mcp:use. These requirements remain additional to workspace role, selected-record visibility and applicable viewAny checks.
