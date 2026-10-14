---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the title or context
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product saves the discussion
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: changes
    facts:
    - Title
    - Context
  contexts:
    web:
      place: web::signed-in::discussion-form
---

# Edit a discussion's context

## Trigger

The author, a thread admin or an allowed member updates the context as the discussion moves on.

## Outcome

The discussion shows the new title and context, and earlier versions can be compared.
