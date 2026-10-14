---
domain: profile
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/user_service.rb#deactivate
- kind: code
  role: implementation
  target: app/workers/deactivate_user_worker.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/user_service.js
---

# Deactivate account

Stop all emails and leave every group while keeping one's name on past discussions and decisions. Votes already cast stay in polls still open.
