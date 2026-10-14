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
---

# Hide poll template

Keep a poll template without offering it to people starting a poll.
