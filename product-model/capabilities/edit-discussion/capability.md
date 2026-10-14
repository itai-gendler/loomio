---
domain: discussions
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/discussion_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/discussions_controller.rb
---

# Edit discussion

Change a discussion's title and context, optionally summarizing what changed for the people notified.
