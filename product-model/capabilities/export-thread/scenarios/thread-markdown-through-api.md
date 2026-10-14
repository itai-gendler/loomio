---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks for a thread as Markdown
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product returns the thread as Markdown with what the User may see
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  - entity: discussion
    effect: reads
    facts:
    - Title
    - Context
  contexts:
    web:
      place: api
---

# Get a thread as Markdown through the API

## Trigger

An integration or AI agent acting as a person reads a thread.

## Outcome

The integration has the complete thread as Markdown.
