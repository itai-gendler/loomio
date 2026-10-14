---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Translate below a comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product has the text translated into the User's language by the translation service and shows it in place
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts:
    - Body
  - entity: user
    effect: reads
    facts:
    - Language
  contexts:
    web:
      place: web::signed-in::thread
---

# Translate a comment

## Trigger

Someone reads a comment written in another language.

## Outcome

The comment is shown in the reader's language in place of the original.
