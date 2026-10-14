---
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/search_controller.rb
- kind: code
  role: implementation
  target: app/services/search_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/search_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/overview/finding-content.md
---

# Search

Find discussions, comments, polls, votes and outcomes one may read, across groups or within one group or organization.
