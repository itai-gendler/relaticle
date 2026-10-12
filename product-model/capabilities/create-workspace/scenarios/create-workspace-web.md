---
kind: primary
routes:
  main: Create an owned Workspace
steps:
- text: Supply the working scope identity and referral information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::create-workspace
  actor: workspace-viewer
- text: The Product creates the owned workspace, initializes its balance and carries the actor into required setup
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
      place: customer-web::workspace::create-workspace
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Actions/Jetstream/CreateWorkspace.php
- kind: code
  role: implementation
  target: app/Policies/WorkspacePolicy.php
---

# Create an owned Workspace

## Trigger

The Account supplies a workspace name, optional handle and referral information.

## Outcome

The Workspace is retained as Active with the Account as owner, its configured default Plan and required Setup Step, and the Account’s persisted web selection changes to it. First ownership sets Personal Workspace; billing-enabled creation starts the inspected trial.
