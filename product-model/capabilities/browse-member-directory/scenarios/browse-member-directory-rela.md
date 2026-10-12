---
kind: primary
routes:
  main: "Discover member directory \u2014 rela"
steps:
- text: Request the member directory
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
- text: The Product returns the working scope name and email directory
  kind: product
  entities:
  - entity: account
    effect: reads
    facts:
    - Name
    - Email
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-viewer
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/ListWorkspaceMembersTool.php
---

# Discover member directory — rela

## Trigger

The actor requests workspace member names and email addresses.

## Outcome

The names and emails are returned. Rela returns at most 50 members with the inspected directory result.
