---
kind: alternative
routes:
  web: Web
steps:
- text: The User writes a task list item that mentions an assignee and optionally sets a due date and reminder
  kind: actor
  actor: user
  entities:
  - entity: task
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product adds the comment and records the task for its assignees
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: creates
    to: Visible
    facts:
    - Body
    - Reply to
    - Replies
  - entity: task
    effect: creates
    to: Open
    facts:
    - Name
    - Due date
    - Reminder
    with: comment
  contexts:
    web:
      place: web::signed-in::thread
---

# Post a comment with a task

## Trigger

Someone writes a task list item that @mentions the person who should do it.

## Outcome

The comment shows the task, and it appears on each assignee's Tasks page.
