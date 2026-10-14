---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Tasks
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::tasks
- text: The Product lists the tasks the User wrote, did or is assigned, from items the User may read
  kind: product
  actor: user
  entities:
  - entity: task
    effect: reads
    facts:
    - Name
    - Due date
  contexts:
    web:
      place: web::signed-in::tasks
---

# Open your tasks

## Trigger

Someone checks what they have to do.

## Outcome

The person sees their tasks with due dates.
