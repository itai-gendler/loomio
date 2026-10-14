---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Email notifications
permits:
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#set_volume
---

# People choose only their own notification settings for a group

Admins cannot change other people's notification settings.
