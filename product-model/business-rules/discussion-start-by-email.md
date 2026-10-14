---
appliesTo:
- type: entity
  id: discussion
  effect: creates
  contexts:
  - place: email
permits:
- actors:
  - user
  when:
  - entity: server-settings
    fact: Threads from email
    is: Enabled
references:
- kind: code
  role: implementation
  target: app/services/received_email_service.rb#route
---

# Discussions start by email only while the server allows it and the sender is a member

The sender's address must belong to a member of the group or be an alias the group recognizes for one.
