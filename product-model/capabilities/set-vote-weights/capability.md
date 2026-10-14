---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb#set_weight
- kind: code
  role: implementation
  target: app/services/stance_service.rb#reset_weights
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/weighted_voting/index.md
---

# Set vote weights

Change how much one voter's vote counts in a poll that uses vote weights, or set every voter's weight from member weights or to one value.
