---
kind: primary
routes:
  main: Dedicated attachment adds entries
steps:
- text: Attach the additional selected sale record
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
- text: The Product adds the requested link without detaching existing entries
  kind: product
  entities:
  - entity: task
    effect: changes
    facts:
    - Opportunities
  contexts:
    main:
      place: agent-access::task
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Actions/Task/AttachTaskRelationships.php
---

# Dedicated attachment adds entries

## Trigger

A Task already links one Opportunity and another is selected for attachment.

## Outcome

The new Opportunity is attached and the existing link remains; neither linked record is changed.
