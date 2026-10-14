---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/outcome_service.rb#create
- kind: code
  role: implementation
  target: app/models/ability/outcome.rb
- kind: code
  role: implementation
  target: app/models/outcome.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/intro_to_decisions/index.md
---

# Share outcome

State what was decided once a poll has closed, optionally with a review date and the people to notify. The outcome appears above the results.
