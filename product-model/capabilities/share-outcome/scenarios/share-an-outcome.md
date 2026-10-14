---
kind: primary
routes:
  web: Web
steps:
- text: The User writes the outcome, sets a review date and picks people to notify
  kind: actor
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product publishes the outcome above the results and notifies the chosen people with the results and the outcome
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

# Share an outcome

## Trigger

A poll has closed and someone records what the group decided.

## Outcome

The outcome shows above the results and the chosen people have the results and the outcome by email.
