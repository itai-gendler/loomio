---
availability:
- place: web::public
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: vue/src/components/group/page.vue
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/groups_controller.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/discussions_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/integrations/api/user-api.md
---

# View group

Open a group's page: its name, description, and the threads and polls the viewer may read.
