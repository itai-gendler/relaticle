---
kind: primary
result: achieved
routes:
  main: Configured Workspace Home
steps:
- text: Supply the new name and handle
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::create-workspace
  actor: workspace-owner
  capability: create-workspace
- text: The Product retains the owned workspace and carries the same Account into required setup
  kind: product
  entities:
  - entity: workspace
    effect: creates
    facts:
    - Name
    - Handle
    - Logo
    - Personal Workspace
    - Use Case
    - Use Case Context
    - Other Use Case
    - Setup Step
    - Referral Source
    - Referral Detail
    - Referral Prompt
    - Plan
    - Trial Ends
    - Scheduled Deletion
    to: Active
  - entity: credit-balance
    effect: creates
    facts:
    - Remaining
    - Used
    - Purchased
    - Period Start
    - Period End
    - Workspace
    to: Available
    with: workspace
  - entity: account
    effect: changes
    facts:
    - Current Workspace
  - entity: custom-field
    effect: creates
    facts:
    - Name
    - Code
    - Record Type
    - Field Type
    - Active
    - System Defined
    - Required
    - Order
    - Workspace
    to: Present
    with: workspace
  - entity: custom-field-option
    effect: creates
    facts:
    - Name
    - Order
    - Field
    to: Present
    with: custom-field
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
  capability: create-workspace
- text: Complete the required setup steps and finish the optional invitation step
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::workspace-setup
  actor: workspace-owner
  capability: set-up-workspace
- text: The Product completes setup and carries the same identity to its configured working destination
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
      place: customer-web::workspace::home
  actor: workspace-owner
  capability: set-up-workspace
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Filament/Pages/SetupWorkspace.php
- kind: code
  role: implementation
  target: app/Filament/Pages/Concerns/RunsInviteStep.php
- kind: code
  role: implementation
  target: app/Actions/Onboarding/CreateSetupConversation.php
---

# Configured Workspace Home

## Trigger

The signed-in Account creates an owned Workspace through the inspected setup path.

## Outcome

The same Account is the owner of the created Workspace; setup is complete and Home is reached. Create → required setup is the two-Capability hand-off; arriving alone does not claim an additional used ability.

## Decision points

### Home destination

Which workspace reaches Home after the inspected setup?

- An additional nonpersonal workspace → Home.
- A personal workspace without an eligible setup conversation → Home.
