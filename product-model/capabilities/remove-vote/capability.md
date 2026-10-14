---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb#uncast
- kind: code
  role: implementation
  target: vue/src/shared/services/poll_service.js
---

# Remove your vote

Withdraw one's vote from an open poll that is not anonymous, becoming undecided again.
