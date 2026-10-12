---
appliesTo:
- type: entity
  id: workspace-invitation
  effect: reads
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
  - verb: contains
    entity: membership
  - verb: holds
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-owner
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-admin
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-member
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
- related:
  - verb: receives
    entity: account
  - verb: has identity
    entity: workspace-viewer
  when:
  - fact: Email
    is:
      entity: account
      fact: Email
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

# Managers or matching recipients may read invitations

Manager roster reads use Members Manage. Incoming/acceptance reads instead require the addressed canonical Account email and current valid invitation; possession alone does not grant another Account access.

A valid opaque-link holder whose signed-in email mismatches receives the wrong-account confirmation result, including invited email and workspace name plus their own current email. It does not disclose the manager roster or allow acceptance; the actual URL credential proof is required for this limited preconfirmation disclosure.
