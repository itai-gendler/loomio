---
appliesTo:
- type: entity
  id: thread
  effect: changes
  facts:
  - Private
permits:
- related:
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Thread admin
    is: true
references:
- kind: code
  role: implementation
  target: app/services/group_service/privacy_change.rb
---

# Only admins change the privacy of a group's threads, and thread admins when moving a thread

Threads change privacy when an admin changes the group's privacy or discussion privacy, and when a thread admin moves a thread to another group or makes it direct.
