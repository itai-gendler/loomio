---
kind: primary
routes:
  web: Web
steps:
- text: A task's reminder time has arrived and it is not done
  kind: condition
  unattended: true
  entities:
  - entity: task
    effect: reads
    facts:
    - Reminder
  contexts:
    web:
      place: web::signed-in::tasks
- text: The Product emails each assignee a reminder
  kind: product
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

# Assignees are reminded of a task

## Trigger

A task's reminder time arrives while it is not done.

## Outcome

Each assignee has an email reminding them of the task.
