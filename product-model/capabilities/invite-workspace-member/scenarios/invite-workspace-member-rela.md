---
kind: primary
routes:
  main: Invite workspace member — rela
steps:
- text: Supply the addressed invitation request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-admin
- text: The Product retains the separately decidable invitation proposal
  kind: product
  entities:
  - entity: workspace-invitation-proposal
    effect: creates
    facts:
    - Proposed Emails and Roles
    - Requester
    - Workspace
    - Conversation
    - Turn
    - Valid Until
    - Decision
    - Decision Time
    - Dependencies
    - Results
    to: Proposed
  contexts:
    main:
      place: customer-web::workspace::chat
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

# Invite workspace member — rela

## Trigger

The actor supplies canonical addressed invitation entries and an assignable role.

## Outcome

The invitation proposal is retained; no invitation is sent until its own decision.
