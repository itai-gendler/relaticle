---
kind: primary
routes:
  main: Complete setup with optional invitations
steps:
- text: Supply optional addressed entries and finish setup
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product completes setup and issues the optional valid invitation entries
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Setup Step
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
      place: customer-web::workspace::home
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsInviteStep.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/MoveWorkspaceSetup.php
- kind: code
  role: implementation
  target: app/Actions/Jetstream/InviteWorkspaceMember.php
---

# Complete setup with optional invitations

## Trigger

An additional owned Workspace is at Invite after its use-case choices are retained.

## Outcome

Setup Step is cleared before invitations are issued and Home is reached. Valid entries retain their separately authorized invitations. If sending fails, a warning is shown without undoing completed setup or prior successfully issued entries.
