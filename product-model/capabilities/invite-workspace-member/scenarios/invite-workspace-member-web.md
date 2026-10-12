---
kind: primary
routes:
  main: Invite workspace member — web
steps:
- text: Supply the addressed invitation request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
- text: The Product retains the issued invitation and schedules its configured mail
  kind: product
  entities:
  - entity: workspace-invitation
    effect: creates
    facts:
    - Email
    - Role
    - Inviter
    - Workspace
    - Issued At
    - Expires At
    - Invitation Credential
    to: Issued
  contexts:
    main:
      place: customer-web::workspace::members
  actor: workspace-admin
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/InviteWorkspaceMember.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/ResendWorkspaceInvitation.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Workspace/InviteWorkspaceMemberTool.php
---

# Invite workspace member — web

## Trigger

The actor supplies canonical addressed invitation entries and an assignable role.

## Outcome

The invitation is retained with its hashed opaque credential and seven-day expiry; configured mail is queued after commit.
