---
kind: validation
routes:
  main: Member cross-record activity refusal
steps:
- text: A Member requests changes across records without selecting one subject
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::workspace::chat
  actor: workspace-member
references:
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
---

# Member cross-record activity refusal

## Trigger

A Member requests activity without a selected record.

## Outcome

The cross-record request is refused; selecting an individually visible subject remains a distinct query.
