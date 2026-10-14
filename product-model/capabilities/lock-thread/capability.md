---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#lock
- kind: code
  role: implementation
  target: vue/src/shared/services/topic_service.js
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
---

# Lock thread

Lock a thread so nobody comments in it or changes it, once its active polls have closed.
