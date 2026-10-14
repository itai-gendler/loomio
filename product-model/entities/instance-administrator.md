---
kind: person
acts: internal
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: code
  role: implementation
  target: app/models/ability/group_state.rb
---

# Instance administrator

A person the Loomio server marks as an instance administrator. Beyond what their memberships allow, an instance administrator may start top-level groups when group creation is turned off for everyone else, delete any group and remove anyone from a group. Groups whose subscription has lapsed stay fully usable to them.
