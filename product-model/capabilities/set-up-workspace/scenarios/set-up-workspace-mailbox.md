---
kind: primary
routes:
  main: Set up Workspace — mailbox
steps:
- text: Connect a mailbox through an offered provider and approve access at the provider
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product returns to setup with the connected mailbox and moves setup to Sharing
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Setup Step
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: Choose what other members see of the mailbox's email
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product keeps the chosen sharing level on the connected mailbox and moves setup to Use Case
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Setup Step
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: Save the chosen use case and its applicable context inputs
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product saves the use-case information and moves setup to Invite
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Use Case
    - Use Case Context
    - Other Use Case
    - Setup Step
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: Finish the invitation step without additional entries
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product completes setup and carries the actor to Home
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Setup Step
  contexts:
    main:
      place: customer-web::workspace::home
  actor: workspace-owner
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsMailboxSteps.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/SaveOnboardingSharing.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/MoveWorkspaceSetup.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/SaveOnboardingUseCase.php
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsInviteStep.php
---

# Set up Workspace — mailbox

## Trigger

An additional owned Workspace begins setup at Email, and at least one mailbox provider is offered.

## Outcome

The connected mailbox keeps the chosen sharing level, Metadata only or Subject (Metadata only is preselected). Use Case, valid context selections and any Other response are retained as in use-case setup; setup proceeds to Invite and completion clears Setup Step, carrying the same Account to Home.

## Edge cases

- Skipping the mailbox, after confirming, moves setup from Email straight to Use Case without the Sharing step.
- With no mailbox provider configured, opening setup at Email or Sharing moves it to Use Case.
- At Use Case without a connected mailbox, the actor may go back to Email.
- A stale already-settled setup step is not saved again; the process returns to its current setup destination.
