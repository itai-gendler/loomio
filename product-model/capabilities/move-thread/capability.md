---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#move
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: code
  role: implementation
  target: app/models/ability/group.rb
---

# Move thread

Move a discussion's thread to another group the mover may start discussions in, or make it a direct discussion. The thread's privacy follows its new group.
