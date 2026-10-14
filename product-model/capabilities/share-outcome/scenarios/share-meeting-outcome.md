---
kind: alternative
routes:
  web: Web
steps:
- text: The poll is a time poll
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Poll type
  contexts:
    web:
      place: web::signed-in::thread
- text: The User picks the chosen date, enters the location and writes the outcome
  kind: actor
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product publishes the outcome with a calendar invitation for the chosen date
  kind: product
  actor: user
  entities:
  - entity: outcome
    effect: creates
    to: Current
    facts:
    - Statement
    - Review date
    - Chosen option
    - Event location
  contexts:
    web:
      place: web::signed-in::thread
---

# Share the outcome of a time poll

## Trigger

A time poll has closed and a meeting time is settled.

## Outcome

The outcome names the chosen date and place and the notification carries a calendar invitation.
