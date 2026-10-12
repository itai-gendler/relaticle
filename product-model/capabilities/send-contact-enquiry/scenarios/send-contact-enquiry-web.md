---
kind: primary
routes:
  main: Send contact enquiry
steps:
- text: Submit the enquiry
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::contact
  actor: visitor
- text: The Product validates input and attempts configured mail delivery
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
---

# Send contact enquiry

## Trigger

A Visitor supplies valid name, email, optional company and a message of 20–5,000 characters.

## Outcome

After the configured mail call returns, the submitted process redirects with success. No retained customer Enquiry or delivery guarantee is asserted.
