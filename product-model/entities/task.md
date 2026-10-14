---
references:
- kind: code
  role: implementation
  target: app/models/task.rb
- kind: code
  role: implementation
  target: app/services/task_service.rb
- kind: code
  role: implementation
  target: app/models/ability/task.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/tasks/index.md
---

# Task

An action written as a task list item in a discussion's context, comment, poll or outcome. People @mentioned in it are its assignees; it can carry a due date with an email reminder.

## Information kept

- **Name** — the action
- **Due date** — when it is due
- **Reminder** — when assignees are emailed a reminder
- **Done by** — who marked it done, and when

## States

### Open

The task is not done.

### Done

Someone marked it done.
