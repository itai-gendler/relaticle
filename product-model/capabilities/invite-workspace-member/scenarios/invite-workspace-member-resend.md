---
kind: primary
routes:
  main: "Invite workspace member \u2014 resend"
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
    effect: changes
    facts:
    - Invitation Credential
    - Expires At
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

# Invite workspace member — resend

## Trigger

The actor supplies canonical addressed invitation entries and an assignable role.

## Outcome

The invitation credential and seven-day deadline are rotated on resend, subject to the one-minute resend limit.
