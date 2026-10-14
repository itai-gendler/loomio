---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb
- kind: code
  role: implementation
  target: app/services/anonymous_ballot_service.rb#create
- kind: code
  role: implementation
  target: app/models/stance.rb
- kind: code
  role: implementation
  target: app/models/concerns/validates_ballot.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/overview/how-to-participate.md
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/anonymous_voting/index.md
---

# Vote

Respond to an open poll in the way its type asks: choose a position or options, score, rank or allocate, or state availability, with a reason where the poll allows one. People change their vote until the poll closes, except in anonymous polls.
