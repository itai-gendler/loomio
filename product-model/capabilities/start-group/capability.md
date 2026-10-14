---
domain: group-settings
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_service.rb#create
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: vue/src/components/group/new_form.vue
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/starting_a_group/index.md
---

# Start group

Start a new top-level group, which becomes an organization, or a subgroup inside an organization. Whoever starts it becomes its first admin, and a new top-level group runs under the free plan until another is chosen.
