---
kind: primary
routes:
  web: Web
steps:
- text: The User selects tags to add or remove beside the thread's title
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts:
    - Name
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the thread's tags
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Tags
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Change a thread's tags

## Trigger

Someone who may edit a discussion or poll categorizes it.

## Outcome

The thread shows the chosen tags and appears under them on the group page.
