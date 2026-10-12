---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Title
  - Status
  - Priority
  - Due Date
  - Description
  - Assignees
  - Companies
  - People
  - Opportunities
  - Order
  - Additional Values
  - Changed At
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
- unattended: true
references:
- kind: code
  role: implementation
  target: app/Policies/TaskPolicy.php
- kind: code
  role: implementation
  target: app/Enums/WorkspaceRole.php
---

# Workspace writers may change record information — task

The grant follows this task’s Workspace: its owner through ownership, or its own Membership through the assigned role. This selects supplied own facts, links, assignments, completion and board values. Imported changes execute under the original process context without a later per-record policy recheck. On REST token-bearing requests the actual selected credential must hold the corresponding read/create/update/delete ability; Passport cookie credentials are refused. On MCP OAuth the selected credential must hold mcp:use, while personal tokens require the operation ability. Session-only REST calls follow their inspected policy path. Ownership of some other credential never qualifies the request.
