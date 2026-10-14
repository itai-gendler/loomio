---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#close
- kind: code
  role: implementation
  target: app/services/poll_service.rb#do_closing_work
- kind: code
  role: implementation
  target: app/workers/close_expired_poll_worker.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/poll_service.js
---

# Close poll

End voting. A poll closes by itself at its closing time, and a poll admin can close it early. Closing counts an STV Election and publishes vote reasons that were hidden until closing.
