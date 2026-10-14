---
availability:
- place: web::public
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: code
  role: implementation
  target: app/models/topic.rb#visible_to
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/threads_controller.rb
---

# View thread

Read a thread: the discussion or standalone poll that opened it, comments, polls with the results the reader may see, votes and outcomes, in order.
