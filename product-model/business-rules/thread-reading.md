---
appliesTo:
- type: entity
  id: thread
  effect: reads
permits:
- actors:
  - visitor
  - user
  when:
  - fact: Private
    is: false
- related:
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
- related:
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Guest
    is: true
references:
- kind: code
  role: implementation
  target: app/models/topic.rb#visible_to
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
---

# Only the group's members and the thread's guests read a private thread

A public thread is readable by anyone. Members of the parent group also read a subgroup's private threads when the subgroup lets parent members see discussions. Nobody reads a deleted thread or the threads of a deleted group.
