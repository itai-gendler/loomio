---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/task_service.rb#update_done
- kind: code
  role: implementation
  target: app/models/ability/task.rb
---

# Mark task as done

Tick a task as done, while editing the text, while reading it as an assignee, or from the Tasks page.
