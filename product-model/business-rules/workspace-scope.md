---
appliesTo:
- type: entity
  id: company
  effect: reads
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
  effect: reads
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
  effect: reads
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
  effect: reads
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
  effect: reads
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
references:
- kind: code
  role: implementation
  target: app/Models/Scopes/WorkspaceScope.php
- kind: code
  role: implementation
  target: app/Queries/Concerns/ListsEntity.php
---

# CRM reads fail closed without a bound Workspace

CRM reads use CurrentWorkspace. An unbound scope returns no rows. Explicit tenant-filtered queries remove the scope only while retaining their own workspace predicate.
