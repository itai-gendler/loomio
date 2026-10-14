---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Name
  - Handle
  - Description
  - Privacy
  - Discussion privacy
  - How people join
  - Joining prompt
  - Listed in directory
  - Parent members can see discussions
  - Members can add members
  - Members can add guests
  - Members can announce
  - Members can start discussions
  - Non-members can start discussions
  - Members can edit discussions
  - Members can edit comments
  - Members can delete comments
  - Members can start polls
  - Members can create subgroups
  - Members can create tags
  - Members can create templates
  - Admins can edit member comments
permits:
- related:
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/permissions.md
---

# Only admins change a group's settings

A group's profile, privacy, joining and member permissions are changed by its admins. Enabling a member permission extends that one action to ordinary members; it never makes them admins.
