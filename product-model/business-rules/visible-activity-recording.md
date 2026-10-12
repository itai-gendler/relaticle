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
  effect: changes
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
  effect: changes
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
  effect: changes
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
  effect: changes
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
  effect: removes
- type: entity
  id: person
  effect: removes
- type: entity
  id: opportunity
  effect: removes
- type: entity
  id: task
  effect: removes
- type: entity
  id: note
  effect: removes
- type: entity
  id: import
  effect: changes
- type: entity
  id: activity
references:
- kind: code
  role: implementation
  target: app/Models/ActivityLog/Activity.php
- kind: code
  role: implementation
  target: packages/Chat/src/Tools/Activity/ListActivityTool.php
- kind: code
  role: implementation
  target: app/Mcp/Tools/ListActivityTool.php
---

# Displayed activity records CRM changes and import summaries

Recorded operations retain displayed Actor, Subject, Change, Source, Time and Workspace, with inspected import summary information. Queries group complete saves and exclude absent subjects.
