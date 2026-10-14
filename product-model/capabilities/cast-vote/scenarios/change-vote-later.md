---
kind: alternative
routes:
  web: Web
steps:
- text: At least 15 minutes have passed since the vote, or someone replied to it
  kind: condition
  actor: user
  entities:
  - entity: vote
    as: earlier
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
    as: earlier
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product keeps the earlier vote in the history and records the new one as current
  kind: product
  actor: user
  entities:
  - entity: vote
    as: earlier
    effect: changes
    from: Cast
    to: Superseded
    facts: []
  - entity: vote
    as: current
    effect: creates
    to: Cast
    facts:
    - Choices
    - Reason
    - Weight
    - Cast at
    - Invited by
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Change a vote after a while

## Trigger

A voter changes their mind after 15 minutes, or after someone replied to their vote.

## Outcome

The new vote counts and the earlier one stays visible in the vote's history.
