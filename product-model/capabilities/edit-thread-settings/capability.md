---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
---

# Edit thread settings

Choose how a thread's replies are arranged and whether it allows comments, reactions and concurrent polls, and its comment length limit. The settings apply to everyone in the thread.
