---
kind: alternative
routes:
  web: Web
steps:
- text: The User changes the context, writes what has changed and picks people to notify
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product saves the discussion, adds an edited item to the thread and notifies the chosen people with the summary
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: changes
    facts:
    - Title
    - Context
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
---

# Edit a discussion and notify people

## Trigger

The editor wants people to know what changed.

## Outcome

The thread shows that the context was edited and the chosen people have the summary.
