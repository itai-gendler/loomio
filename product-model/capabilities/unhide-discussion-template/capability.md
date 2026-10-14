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

# Unhide discussion template

Offer a hidden discussion template again.
