---
appliesTo:
- type: entity
  id: activity
  effect: reads
  contexts:
  - place: customer-web::workspace::chat
  - place: customer-web::workspace::workspace-activity
  - place: agent-access::workspace-activity
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
- configuredBy: membership
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
  target: app/Models/User.php#workspaceCapabilities
- kind: code
  role: implementation
  target: app/Actions/Jetstream/UpdateWorkspaceMemberRole.php#update
- kind: code
  role: implementation
  target: app/Livewire/App/Workspaces/WorkspaceMembers.php#updateWorkspaceRoleAction
- kind: code
  role: implementation
  target: app/Filament/Pages/Workspace/ActivityLog.php#canAccess
- kind: code
  role: implementation
  target: app/Policies/OpportunityPolicy.php#view
- kind: code
  role: implementation
  target: app/Mcp/Tools/Concerns/ChecksTokenAbility.php#denyIfTokenCannot
---

# Selected-record history requires record access; cross-record activity requires Owner or Admin authority

Authorization follows the actual requested query and the workspace in which it executes.

The ownership alternatives follow the queried Activity’s Workspace to its owning Account. Ownership of another workspace does not qualify. Owner authority requires no Membership entry.

The explicit Admin alternatives require the acting person’s own Membership in that Workspace to hold Admin. For an External AI Agent, authority follows the Account authenticated by the actual connection, not another Account or another credential belonging to the person.

The configured Membership alternative evaluates the authenticated person’s actual retained assignment in the query workspace, using the shipped WorkspaceRole capability matrix:

- For Rela selected-record history, after transport input normalization, record_type and record_id identify an existing visible record in the current workspace. Its view policy requires Records View. Admin, Member and Viewer assignments supply that capability.
- For Rela queries without a normalized record_id, including record-type-only queries, the assignment must supply Activity View. Only Admin does so.
- Native Workspace Activity reads require Activity View, irrespective of filters applied to the page.
- MCP evaluates its validated request’s actual record-id branch. A selected record requires its view policy; a request without record_id, including a type-only request, requires Activity View. Its applicable viewAny checks also remain required.

A missing or unrecognized Membership role grants nothing through the configuration alternative. Membership in another workspace grants nothing. Customers assign the retained role; they do not configure this dispatch decision or the shipped role-to-capability matrix. The configured alternative never permits a Viewer or Member cross-record query.

Record lookup, subject visibility and workspace query boundaries remain mandatory. Passing an ownership or Admin alternative does not bypass them. For selected-record queries, a soft-deleted or missing subject is not returned. Cross-record queries require no selected subject and may retain activity for soft-deleted subjects that still exist.

On REST token-bearing requests the actual selected credential must hold the corresponding read/create/update/delete ability; Passport cookie credentials are refused. On MCP OAuth the selected credential must hold mcp:use, while personal tokens require the operation ability. Session-only REST calls follow their inspected policy path. Ownership of some other credential never qualifies the request.

For the inspected MCP activity read, the actual current persisted personal token must hold read; a Passport access token must hold mcp:use. Those current-credential checks remain additional conditions on every applicable alternative, including configured Membership. Identity authentication, email verification where required, and ordinary request validation remain distinct from this authorization decision.
