---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/polls_controller.rb#votes
- kind: code
  role: implementation
  target: vue/src/components/poll/votes_page.vue
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/anonymous_voting/index.md
---

# View votes

See each vote in a poll with its reason and weight, filtered by option, or for an anonymous poll who took part once results are available.
