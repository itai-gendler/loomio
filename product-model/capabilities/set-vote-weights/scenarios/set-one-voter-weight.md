---
kind: primary
routes:
  web: Web
steps:
- text: The User selects the weight beside a voter in Manage voters and enters a new one
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the weight and recalculates the results
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    facts:
    - Weight
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Change one voter's weight

## Trigger

A poll admin corrects someone's weight in Manage voters.

## Outcome

The voter's vote counts with the new weight and the results are recalculated.

## Edge cases

- Weights are zero or more, with up to three decimal places.
