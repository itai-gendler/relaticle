---
kind: primary
routes:
  board: Opportunities board
steps:
- text: Move the selected card to another column and choose its position
  kind: actor
  actor: workspace-member
  entities: []
  contexts:
    board:
      place: customer-web::workspace::opportunities
- text: The Product saves the Opportunity column value and order together
  kind: product
  actor: workspace-member
  entities:
  - entity: opportunity
    effect: changes
    facts:
    - Stage
    - Order
    - Changed At
  contexts:
    board:
      place: customer-web::workspace::opportunities
references:
- kind: code
  role: implementation
  target: app/Filament/Resources/OpportunityResource/Pages/OpportunitiesBoard.php#moveCard
- kind: code
  role: implementation
  target: app/Policies/OpportunityPolicy.php#update
---

# Edit Opportunity Stage and Order on the board

## Trigger

The person moves an existing Opportunity card to a configured Stage column and chooses its position on the Opportunities board.

## Outcome

Stage is set to the resolved destination option and Order to the calculated position within one transaction. The successful movement is reported. Company and Point of Contact remain unchanged. Reordering within the current column preserves its selected Stage.
