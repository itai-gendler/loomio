---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#set_weights
- kind: code
  role: implementation
  target: vue/src/components/group/member_weights_page.vue
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/weighted_voting/index.md
---

# Edit vote weights

Set the vote weight each member brings into the polls they are added to.
