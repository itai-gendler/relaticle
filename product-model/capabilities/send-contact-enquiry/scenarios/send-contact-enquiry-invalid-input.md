---
kind: validation
routes:
  main: Invalid contact input
steps:
- text: Required enquiry fields, valid email or submitted text length fail validation; the route also has its configured
    throttle and honeypot.
  kind: condition
  entities: []
  contexts:
    main:
      place: customer-web::public::contact
- text: Submit the request
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::contact
  actor: visitor
- text: The Product returns the stated refusal without the guarded write
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::public::contact
  actor: visitor
references:
- kind: code
  role: implementation
  target: app/Http/Controllers/ContactController.php
- kind: code
  role: implementation
  target: routes/web.php
---

# Invalid contact input

## Trigger

Required enquiry fields, valid email or message length fail validation; the route also has its configured throttle and honeypot.

## Outcome

Validation reports the problem and the mail submission is not performed.
