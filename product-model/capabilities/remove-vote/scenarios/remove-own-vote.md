---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Remove your vote
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
- text: The Product keeps the vote in the history and leaves the User undecided
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
    to: Undecided
    facts:
    - Weight
    - Invited by
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Remove your vote

## Trigger

A voter wants to withdraw their vote while the poll is open.

## Outcome

The voter is undecided again and the earlier vote stays in the history.
