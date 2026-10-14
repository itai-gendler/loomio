---
kind: edge
routes:
  web: Web
steps:
- text: No translation service is configured
  kind: condition
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User reads a comment in another language
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no Translate action
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Translation is not offered without a translation service

## Trigger

The server has no translation service configured.

## Outcome

No Translate action is shown.
