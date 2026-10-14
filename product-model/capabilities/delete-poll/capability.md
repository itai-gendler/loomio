---
domain: polls
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#discard
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/polls_controller.rb
---

# Delete poll

Delete a poll. Its place in the thread shows it was removed.
