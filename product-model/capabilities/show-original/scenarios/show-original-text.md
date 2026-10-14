---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Original
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product shows the original text
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts:
    - Body
  contexts:
    web:
      place: web::signed-in::thread
---

# Show the original text

## Trigger

Someone wants to read what the author actually wrote.

## Outcome

The original text is shown again.
