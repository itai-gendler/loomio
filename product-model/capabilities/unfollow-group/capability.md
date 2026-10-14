---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_follow_service.rb#destroy
---

# Unfollow group

Stop including a followed Open group in one's catch-up.
