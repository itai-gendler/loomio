---
kind: primary
routes:
  web: Web
steps:
- text: The User ticks the task's checkbox
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::tasks
- text: The Product marks the task done by the User and ticks it in the text
  kind: product
  actor: user
  entities:
  - entity: task
    effect: changes
    from: Open
    to: Done
    facts:
    - Done by
  contexts:
    web:
      place: web::signed-in::tasks
---

# Mark a task as done

## Trigger

An assignee finishes the action.

## Outcome

The task is ticked where it was written and on the Tasks page.
