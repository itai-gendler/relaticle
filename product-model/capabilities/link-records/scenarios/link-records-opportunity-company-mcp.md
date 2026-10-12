---
kind: primary
routes:
  main: Link records — opportunity-company mcp
steps:
- text: Choose the relationship entries to link
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product saves the specified relationship changes
  kind: product
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Company
    - Changed At
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Opportunity/UpdateOpportunity.php
---

# Link records — opportunity-company mcp

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Company link is retained. Company and Point of Contact are independent and need not refer to matching Companies; clearing one preserves the other.
