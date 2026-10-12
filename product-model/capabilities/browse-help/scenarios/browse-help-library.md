---
kind: primary
routes:
  main: Read help library
steps:
- text: Request the help library
  kind: actor
  entities: []
  contexts:
    main:
      place: customer-web::public::help-library
  actor: visitor
- text: The Product returns the shipped help information
  kind: product
  entities: []
  contexts:
    main:
      place: customer-web::public::help-library
  actor: visitor
references:
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
---

# Read help library

## Trigger

Documentation is enabled and a Visitor requests the help library.

## Outcome

The shipped categories, article summaries and searched results are available.
