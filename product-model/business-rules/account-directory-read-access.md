---
appliesTo:
- type: entity
  id: account
  effect: reads
  facts:
  - Name
  - Email
  contexts:
  - place: customer-web::workspace::chat
  - place: agent-access::account-context
permits:
- related:
  - verb: holds
    entity: membership
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: holds
    entity: membership
  - verb: contains
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: owns
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
- related:
  - verb: owns
    entity: workspace
  - verb: owns
    entity: account
  - verb: has identity
    entity: workspace-owner
  - verb: connects
    entity: ai-agent
- related:
  - verb: holds
    entity: membership
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
  - verb: holds
    entity: membership
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
  - verb: owns
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when: *id001
- related:
  - verb: owns
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
  - verb: holds
    entity: membership
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
  - verb: holds
    entity: membership
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
  - verb: owns
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-member
  when: *id002
- related:
  - verb: owns
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
  - verb: holds
    entity: membership
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
  - verb: holds
    entity: membership
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
- related:
  - verb: owns
    entity: workspace
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when: *id003
- related:
  - verb: owns
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
  target: app/Policies/WorkspacePolicy.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/AcceptWorkspaceInvitation.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/RemoveWorkspaceMember.php
---

# Workspace members may discover directory names and emails

Directory disclosure is bounded to members of the request’s current workspace. It is not Members Manage and not private-profile disclosure. On REST token-bearing requests the actual selected credential must hold the corresponding read/create/update/delete ability; Passport cookie credentials are refused. On MCP OAuth the selected credential must hold mcp:use, while personal tokens require the operation ability. Session-only REST calls follow their inspected policy path. Ownership of some other credential never qualifies the request.
