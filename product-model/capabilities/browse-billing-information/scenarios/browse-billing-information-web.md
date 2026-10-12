---
kind: primary
routes:
  main: Read billing information
steps:
- text: Open Billing
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::billing
  actor: workspace-viewer
- text: The Product returns the published billing and credit information
  kind: product
  entities:
  - entity: workspace
    effect: reads
    facts:
    - Name
    - Plan
    - Trial Ends
  - entity: credit-balance
    effect: reads
    facts:
    - Remaining
    - Used
    - Purchased
    - Period Start
    - Period End
    - Workspace
  contexts:
    main:
      place: customer-web::workspace::billing
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Filament/Pages/Billing.php
- kind: code
  role: implementation
  target: app/Services/Billing/HostedWorkspaceAccess.php
---

# Read billing information

## Trigger

The Account opens the current workspace Billing page.

## Outcome

Plan, trial, source-derived billing-access information and AI credit allocation are available. A paused workspace retains this self-service billing destination; purchasing and subscription restoration are separate lifecycles.
