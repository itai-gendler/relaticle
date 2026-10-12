---
kind: validation
routes:
  main: Current credential lacks read
steps:
- text: The current owned token lacks its read ability.
  kind: condition
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
  actor: workspace-viewer
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: rest-api::opportunities
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: app/Http/Middleware/EnsureTokenHasAbility.php
---

# Current credential lacks read

## Trigger

The current personal token lacks its read ability.

## Outcome

The request returns an ability refusal and no CRM results; MCP’s OAuth path instead checks mcp:use.
