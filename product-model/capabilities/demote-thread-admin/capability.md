---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/topic_readers_controller.rb#remove_admin
- kind: code
  role: implementation
  target: app/models/ability/topic_reader.rb
---

# Demote thread admin

Take the thread admin role away from someone in a thread.
