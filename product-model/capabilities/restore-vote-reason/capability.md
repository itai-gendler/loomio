---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb#unredact
---

# Restore vote reason

Show a redacted vote reason again.
