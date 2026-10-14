---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/topic_readers_controller.rb#make_admin
- kind: code
  role: implementation
  target: app/models/ability/topic_reader.rb
---

# Make thread admin

Make someone an admin of one thread, able to manage it and its polls.
