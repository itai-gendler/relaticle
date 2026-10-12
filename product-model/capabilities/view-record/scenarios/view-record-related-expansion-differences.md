---
kind: edge
routes:
  main: Selected relationship expansion differs
steps:
- text: Request the related result
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
- text: The Product returns the MCP bounded related result
  kind: product
  entities:
  - entity: opportunity
    effect: reads
    facts:
    - Name
    - Company
    - Point of Contact
    - Additional Values
  - entity: task
    effect: reads
    facts:
    - Title
  - entity: note
    effect: reads
    facts:
    - Title
  contexts:
    main:
      place: agent-access::opportunity
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/BaseShowTool.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/BaseReadShowTool.php
- kind: code
  role: implementation
  target: app/Http/Controllers/Api/V1/OpportunitiesController.php
---

# Selected relationship expansion differs

## Trigger

An Opportunity is requested with related collections and an unknown include.

## Outcome

MCP returns at most 25 newest records and truncation metadata, ignoring unknown includes. Rela returns at most ten newest related records and errors on unknown includes. REST show does not process arbitrary includes.
