---
kind: primary
routes:
  web: Web
steps:
- text: The outcome's review date has arrived
  kind: condition
  unattended: true
  entities:
  - entity: outcome
    effect: reads
    facts:
    - Review date
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product reminds the outcome's author to review the decision
  kind: product
  entities:
  - entity: outcome
    effect: reads
    facts:
    - Statement
  contexts:
    web:
      place: web::signed-in::thread
---

# The outcome's author is reminded to review it

## Trigger

An outcome's review date arrives.

## Outcome

The outcome's author is reminded to review the decision.
