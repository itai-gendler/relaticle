---
appliesTo:
- type: context
  context:
    place: customer-web::public::contact
references:
- kind: code
  role: implementation
  target: app/Http/Controllers/ContactController.php
- kind: code
  role: implementation
  target: routes/web.php
---

# Contact success follows validation and configured mail return

Contact name/email are required, email uses the traced DNS validation, company is optional, and message length is 20–5,000 characters. Route throttle and honeypot remain. Success redirect follows the configured mail call returning, not a delivery guarantee or a retained Enquiry.
