---
domain: members
availability:
- place: api
references:
- kind: code
  role: implementation
  target: app/controllers/api/b2/memberships_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/integrations/api/user-api.md
---

# Sync members

Bring a group's members in line with a list of email addresses from another system: invite the addresses not yet in the group and, when asked, remove members whose address is not listed.
