---
entities:
- entity: company
  shows:
  - Name
  - Account Owner
  - Domains
  - ICP
  - LinkedIn
  - Additional Values
  - Created At
  - Changed At
- entity: person
  shows:
  - Name
  - Company
  - Emails
  - Phone Numbers
  - Job Title
  - LinkedIn
  - Additional Values
  - Created At
  - Changed At
- entity: opportunity
  shows:
  - Name
  - Company
  - Point of Contact
  - Stage
  - Amount
  - Close Date
  - Additional Values
  - Created At
  - Changed At
- entity: task
  shows:
  - Title
  - Status
  - Priority
  - Due Date
  - Description
  - Assignees
  - Companies
  - People
  - Opportunities
  - Additional Values
  - Created At
  - Changed At
- entity: note
  shows:
  - Title
  - Body
  - Companies
  - People
  - Opportunities
  - Additional Values
  - Created At
  - Changed At
references:
- kind: code
  role: implementation
  target: app/Filament/Exports/BaseExporter.php
---

# Export records

Selection and generated output of the inspected CRM export.
