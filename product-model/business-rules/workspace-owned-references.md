---
appliesTo:
- type: entity
  id: company
  effect: creates
  facts:
  - Name
  - Account Owner
  - Domains
  - ICP
  - LinkedIn
  - Additional Values
  - Workspace
  - Creator
  - Creation Source
  - Created At
  - Changed At
- type: entity
  id: person
  effect: creates
  facts:
  - Name
  - Company
  - Emails
  - Phone Numbers
  - Job Title
  - LinkedIn
  - Additional Values
  - Workspace
  - Creator
  - Creation Source
  - Created At
  - Changed At
- type: entity
  id: opportunity
  effect: creates
  facts:
  - Name
  - Company
  - Point of Contact
  - Stage
  - Amount
  - Close Date
  - Order
  - Additional Values
  - Workspace
  - Creator
  - Creation Source
  - Created At
  - Changed At
- type: entity
  id: task
  effect: creates
  facts:
  - Title
  - Status
  - Priority
  - Due Date
  - Description
  - Assignees
  - Companies
  - People
  - Opportunities
  - Order
  - Additional Values
  - Workspace
  - Creator
  - Creation Source
  - Created At
  - Changed At
- type: entity
  id: note
  effect: creates
  facts:
  - Title
  - Body
  - Companies
  - People
  - Opportunities
  - Additional Values
  - Workspace
  - Creator
  - Creation Source
  - Created At
  - Changed At
- type: entity
  id: company
  effect: changes
  facts:
  - Account Owner
- type: entity
  id: person
  effect: changes
  facts:
  - Company
- type: entity
  id: opportunity
  effect: changes
  facts:
  - Company
  - Point of Contact
- type: entity
  id: task
  effect: changes
  facts:
  - Assignees
  - Companies
  - People
  - Opportunities
- type: entity
  id: note
  effect: changes
  facts:
  - Companies
  - People
  - Opportunities
references:
- kind: code
  role: implementation
  target: app/Support/TenantFkValidator.php
- kind: code
  role: implementation
  target: app/Actions/Task/DetachTaskRelationships.php
---

# Referenced records and new assignees belong to the resolved Workspace

Supplied Company, Person and Opportunity references are checked against the resolved workspace. New Company owners and Task assignees must be workspace users. Dedicated removal of an existing former-member assignment does not require new membership.
