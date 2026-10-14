---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#update_tags
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/tags/index.md
---

# Tag thread

Add the organization's tags to a thread, or take them off. Changes save at once.
