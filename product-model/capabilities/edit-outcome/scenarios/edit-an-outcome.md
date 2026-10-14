---
kind: primary
routes:
  web: Web
steps:
- text: The User edits the outcome
  kind: actor
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the outcome and notifies anyone the User chose
  kind: product
  actor: user
  entities:
  - entity: outcome
    effect: changes
    facts:
    - Statement
    - Review date
    - Chosen option
    - Event location
  contexts:
    web:
      place: web::signed-in::thread
---

# Edit an outcome

## Trigger

Someone corrects what an outcome says.

## Outcome

The outcome shows the change and earlier versions can be compared.
