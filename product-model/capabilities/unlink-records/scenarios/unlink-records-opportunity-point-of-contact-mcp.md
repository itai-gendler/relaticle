---
kind: primary
routes:
  main: Unlink records — opportunity-point-of-contact mcp
steps:
- text: Choose the relationship entries to unlink
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
    - Point of Contact
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

# Unlink records — opportunity-point-of-contact mcp

## Trigger

The actor supplies a relationship change.

## Outcome

The chosen Point of Contact link is cleared without deleting the linked record. Company and Point of Contact are independent and need not refer to matching Companies; clearing one preserves the other.
