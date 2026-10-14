---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#invite
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
---

# Invite people to thread

Invite people into a thread: notify group members, or give people outside the group guest access to this thread alone.
