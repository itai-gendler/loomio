---
domain: templates
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/discussion_template_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/discussion_templates_controller.rb
- kind: code
  role: implementation
  target: app/models/ability/discussion_template.rb
---

# Hide discussion template

Keep a discussion template without offering it to people starting a discussion.
