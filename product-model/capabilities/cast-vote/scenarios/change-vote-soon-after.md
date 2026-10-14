---
kind: alternative
routes:
  web: Web
steps:
- text: The User voted less than 15 minutes ago and nobody has replied to the vote
  kind: condition
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts:
    - Cast at
  contexts:
    web:
      place: web::signed-in::thread
- text: The User selects Change vote and chooses again
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product updates the vote and the results
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    facts:
    - Choices
    - Reason
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Change a vote soon after casting it

## Trigger

A voter changes their mind within 15 minutes and nobody has replied to their vote.

## Outcome

The same vote shows the new choice.
