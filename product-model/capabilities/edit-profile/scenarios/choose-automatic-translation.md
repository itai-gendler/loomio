---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Translate content to my language automatically
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product saves the preference
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Translate automatically
  contexts:
    web:
      place: web::signed-in::profile
---

# Translate content automatically

## Trigger

A person wants other people's writing in their own language without asking each time.

## Outcome

Supported content is shown translated into the person's language.
