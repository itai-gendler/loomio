---
domain: discussions
availability:
- place: web::signed-in
- place: api
- place: email
references:
- kind: code
  role: implementation
  target: app/services/discussion_service.rb#create
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
- kind: code
  role: implementation
  target: app/models/topic.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/starting_a_discussion/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/direct_discussions/index.md
- kind: code
  role: implementation
  target: app/services/received_email_service.rb#route
- kind: code
  role: implementation
  target: app/controllers/api/b2/discussions_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/email/index.md
---

# Start discussion

Start a discussion in a group, or directly with chosen people outside any group, and choose whom to notify. The discussion opens its own thread, and whoever starts it becomes that thread's admin.
