---
appliesTo:
- type: entity
  id: membership
  effect: reads
  facts:
  - Role
  contexts:
  - place: agent-access::account-context
  - place: customer-web::workspace::chat
permits:
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  - verb: connects
    entity: ai-agent
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  - verb: connects
    entity: ai-agent
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
- related:
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  - verb: connects
    entity: ai-agent
references:
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Accounts may read their own current membership role

The context role belongs to the acting credential’s Account in the resolved workspace; ownership is derived separately and does not manufacture an owner Membership.
