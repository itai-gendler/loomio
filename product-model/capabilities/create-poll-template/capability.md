---
domain: templates
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/poll_template_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/poll_templates_controller.rb
- kind: code
  role: implementation
  target: app/models/ability/poll_template.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/poll_templates/index.md
---

# Create poll template

Make a poll template for a group, starting from an example or a blank template.
