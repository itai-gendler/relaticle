---
kind: primary
routes:
  main: Read product information
steps:
- text: Open product information
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::product-information
  actor: visitor
- text: The Product returns the shipped information
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::public::product-information
  actor: visitor
references:
- kind: code
  role: implementation
  target: routes/web.php
---

# Read product information

## Trigger

A Visitor opens the inspected product information.

## Outcome

The inspected CRM, pricing, AI, self-hosting and security information is available.
