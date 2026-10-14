---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/topic_readers_controller.rb#revoke
- kind: code
  role: implementation
  target: app/models/ability/topic_reader.rb
---

# Remove from discussion

Take a guest's access to a thread away.
