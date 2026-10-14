---
appliesTo:
- type: entity
  id: task
  effect: changes
permits:
- related:
  - verb: is-assigned
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/task.rb
---

# Assignees, the task's author and people who may edit its item mark a task done or open

Everyone involved must be able to see the item the task is in.
