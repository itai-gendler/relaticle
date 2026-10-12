---
kind: primary
routes:
  main: Get Account Context
steps:
- text: Request identity context
  kind: actor
  entities: []
  contexts:
    main:
      place: agent-access::account-context
  actor: ai-agent
- text: The Product returns identity, workspace, member directory and current credential abilities
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Email
  - entity: workspace
    effect: reads
    facts:
    - Name
  - entity: membership
    effect: reads
    facts:
    - Role
  - entity: access-token
    effect: reads
    facts:
    - Read Grant
    - Create Grant
    - Update Grant
    - Delete Grant
  contexts:
    main:
      place: agent-access::account-context
  actor: ai-agent
references:
- kind: code
  role: implementation
  target: app/Mcp/Tools/WhoAmiTool.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/Concerns/ChecksTokenAbility.php
---

# Get Account Context

## Trigger

The connected external agent requests the authenticated account context.

## Outcome

Own name/email, current workspace name, role capabilities, workspace member names/emails and the actual current credential’s effective abilities are returned. This does not return a credential secret.
