---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#unpin
---

# Unpin thread

Return a pinned thread to its place among the group's threads.
