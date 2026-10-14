---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/outcome_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/outcome.rb
---

# Edit outcome

Change a shared outcome's statement, review date, chosen option or location, optionally notifying people.
