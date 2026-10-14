---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: vue/src/components/dashboard/page.vue
- kind: code
  role: implementation
  target: app/controllers/api/v1/topics_controller.rb#index
- kind: code
  role: implementation
  target: app/controllers/api/v1/stances_controller.rb#my_stances
---

# View dashboard

See recent threads from all one's groups and direct discussions, and the polls waiting for one's vote.
