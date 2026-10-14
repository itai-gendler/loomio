---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends search words
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: api
- text: The Product returns matching items from threads the User may read
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts:
    - Title
  - entity: comment
    effect: reads
    facts:
    - Body
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: api
---

# Search through the API

## Trigger

An integration acting as a person searches.

## Outcome

The integration has a bounded list of matching items the person may read.
