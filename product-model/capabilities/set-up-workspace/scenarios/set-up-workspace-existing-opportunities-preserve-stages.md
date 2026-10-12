---
kind: edge
routes:
  main: Set up Workspace — existing-opportunities-preserve-stages
steps:
- text: Save the chosen use case and its applicable context inputs
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product saves the use-case information and moves setup to Invite without replacing the existing pipeline
    options
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
  target: app/Actions/Onboarding/SaveOnboardingUseCase.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/ApplyStagePreset.php
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsInviteStep.php
---

# Set up Workspace — existing-opportunities-preserve-stages

## Trigger

An additional owned Workspace is at Use Case. The chosen use case has a preset but the Workspace already has an Opportunity, including a deleted one.

## Outcome

Use Case, valid context selections and any Other response are retained; setup proceeds to Invite and completion clears Setup Step, carrying the same Account to Home. Existing stage options remain unchanged.

## Edge cases

- A stale already-settled setup step is not saved again; the process returns to its current setup destination.
