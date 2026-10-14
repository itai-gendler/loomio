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
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/templates/index.md
---

# Create discussion template

Make a discussion template for a group, starting from an example or a blank template.
