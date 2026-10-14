---
appliesTo:
- type: entity
  id: group
  effect: creates
permits:
- actors:
  - user
  when:
  - entity: user
    fact: Email verified
    is: true
  - fact: Parent group
    absent: true
  - entity: server-settings
    fact: Group creation
    is: Enabled
- actors:
  - instance-administrator
  when:
  - fact: Parent group
    absent: true
- actors:
  - user
  when:
  - entity: user
    fact: Email verified
    is: true
  - fact: Parent group
    present: true
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/extras/app_config.rb#app_features
---

# Verified users start groups, and top-level groups only while group creation is enabled

Starting a top-level group needs a verified email address and group creation enabled on the server, or an instance administrator. A subgroup is started by a verified member of the parent group who is its admin, or by any verified member when the parent lets members create subgroups.
