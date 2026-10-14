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
- text: The poll requires a reason for the chosen option and the reason has fewer than six characters
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Vote reason
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product refuses the vote and asks for a reason
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

# A vote without a required reason is refused

## Trigger

A voter submits without the reason the poll requires for their choice.

## Outcome

The vote is not recorded.

## Edge cases

- Reasons are limited to 500 characters when the poll limits them.
