---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/task_service.rb#update_done
---

# Reopen task

Untick a task that was marked done.
