---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Manage voters, picks people, groups or delegates and chooses whether to notify them
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product gives each person a vote, weighted by their member weight when the poll uses vote weights, and notifies them when asked
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: creates
    to: Undecided
    facts:
    - Weight
    - Invited by
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Add people to vote

## Trigger

A poll admin wants more people to vote.

## Outcome

Each person added holds an undecided vote and, when asked, has been notified.

## Edge cases

- People who held a vote before and were removed get their earlier vote back.
