---
kind: primary
routes:
  main: "Unassign member \u2014 company-owner mcp"
steps:
- text: Choose the identity assignment change
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
- text: The Product saves the assignment change
  kind: product
  entities:
  - entity: company
    effect: changes
    facts:
    - Account Owner
    - Changed At
  contexts:
    main:
      place: agent-access::company
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Company/UpdateCompany.php
---

# Unassign member — company-owner mcp

## Trigger

The actor supplies an assignment change.

## Outcome

The specified Account Owner assignment is removed without deleting the Account.
