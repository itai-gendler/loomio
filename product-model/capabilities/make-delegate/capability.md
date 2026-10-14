---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#make_delegate
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/delegated_voters/index.md
---

# Make delegate

Mark a member as one of the group's delegates, the people invited when a poll is limited to delegates. The member is notified.
