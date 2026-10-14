---
appliesTo:
- type: entity
  id: thread
  effect: changes
  facts:
  - Tags
permits:
- related:
  - verb: opens
    entity: discussion
  - verb: starts
    entity: user
- related:
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Thread admin
    is: true
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
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can edit discussions
    is: true
- related:
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Guest
    is: true
  - fact: Direct
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: code
  role: implementation
  target: app/services/topic_service.rb#update_tags
---

# People who may edit a discussion or poll tag its thread

Applying a tag that does not exist yet also needs permission to create tags.
