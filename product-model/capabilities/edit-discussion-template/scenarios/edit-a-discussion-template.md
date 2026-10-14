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
      place: web::signed-in::discussion-template-form
- text: The Product saves the template
  kind: product
  actor: user
  entities:
  - entity: discussion-template
    effect: changes
    facts:
    - Title
    - Subtitle
    - Help
    - Starts direct discussions
    - Default title
    - Context
    - Tags
    - Invite everyone
    - Suggested poll templates
    - Thread settings
  contexts:
    web:
      place: web::signed-in::discussion-template-form
---

# Edit a discussion template

## Trigger

Someone who may manage the template adapts it.

## Outcome

New discussions start from the changed template; existing ones keep their content.
