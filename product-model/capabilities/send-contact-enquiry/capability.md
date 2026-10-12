---
availability:
- place: customer-web::public
references:
- kind: code
  role: implementation
  target: routes/web.php
- kind: code
  role: implementation
  target: app/Http/Controllers/ContactController.php
- kind: code
  role: implementation
  target: packages/Documentation/src/Http/Controllers/HelpController.php
---

# Send a contact enquiry

Submit a validated enquiry to the configured mail destination and report success after the mail call returns.
