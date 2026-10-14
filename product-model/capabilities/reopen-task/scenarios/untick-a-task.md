---
kind: primary
routes:
  web: Web
steps:
- text: The User unticks the task's checkbox
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::tasks
- text: The Product reopens the task
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    from: Done
    to: Open
    facts:
    - Done by
  contexts:
    web:
      place: web::signed-in::tasks
---

# Reopen a task

## Trigger

A task marked done turns out to need more work.

## Outcome

The task is open again.
