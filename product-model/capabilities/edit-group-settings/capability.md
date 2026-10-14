---
domain: group-settings
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_service.rb#update
- kind: code
  role: implementation
  target: app/services/group_service/privacy_change.rb
- kind: code
  role: implementation
  target: app/models/concerns/group_privacy.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/permissions.md
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
---

# Edit group settings

Change a group's profile, privacy, how people join, and which actions ordinary members and non-members may take. The settings form groups these as Profile, Privacy and Permissions and saves them together.
