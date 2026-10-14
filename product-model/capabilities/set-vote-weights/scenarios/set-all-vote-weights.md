---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Set all vote weights and chooses member weights or a value
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product sets every voter's weight and recalculates the results once
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

# Set all vote weights

## Trigger

A poll admin applies the group's member weights, or one value, to everyone.

## Outcome

Every voter's weight is the chosen one; voters who are not group members get one.
