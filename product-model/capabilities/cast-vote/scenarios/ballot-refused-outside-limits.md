---
kind: validation
routes:
  web: Web
steps:
- text: The User submits a vote
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The choices are too few or too many, a score is out of range, the dots exceed the budget, or the ranking has gaps
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Ballot limits
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product refuses the vote
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# A ballot outside the poll's limits is refused

## Trigger

A voter's choices break the poll's rules.

## Outcome

The vote is not recorded.
