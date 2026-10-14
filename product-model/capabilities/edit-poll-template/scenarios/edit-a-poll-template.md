---
kind: primary
routes:
  web: Web
steps:
- text: The User edits the template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-template-form
- text: The Product saves the template
  kind: product
  actor: user
  entities:
  - entity: poll-template
    effect: changes
    facts:
    - Title
    - Subtitle
    - Help
    - Poll type
    - Example content
    - Options
    - Default settings
  contexts:
    web:
      place: web::signed-in::poll-template-form
---

# Edit a poll template

## Trigger

Someone who may manage the template adapts it.

## Outcome

New polls start from the changed template; existing ones keep their content.
