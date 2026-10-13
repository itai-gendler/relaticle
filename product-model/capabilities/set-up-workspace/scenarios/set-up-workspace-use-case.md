---
kind: primary
routes:
  main: Set up Workspace — use-case
steps:
- text: Save the chosen use case and its applicable context inputs
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
- text: The Product saves the use-case information and moves setup to Invite while applying the empty-pipeline preset
  kind: product
  entities:
  - entity: workspace
    effect: changes
    facts:
    - Use Case
    - Use Case Context
    - Other Use Case
    - Setup Step
  - entity: custom-field-option
    effect: removes
    from: Present
    as: old-stage-option
  - entity: custom-field-option
    effect: creates
    facts:
    - Name
    - Order
    - Field
    to: Present
    as: preset-stage-option
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

# Set up Workspace — use-case

## Trigger

An additional owned Workspace begins setup at Use Case. The selected use case has a stage preset, the Stage definition exists, and there are no Opportunities, including deleted ones.

## Outcome

Use Case, valid context selections and any Other response are retained; setup proceeds to Invite and completion clears Setup Step, carrying the same Account to Home. The stage option preset is retained.

## Edge cases

- A stale already-settled setup step is not saved again; the process returns to its current setup destination.
