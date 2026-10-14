---
appliesTo:
- type: entity
  id: group
  effect: reads
  facts:
  - Name
  - Description
permits:
- actors:
  - visitor
  - user
  when:
  - fact: Privacy
    is: Open
- actors:
  - visitor
  - user
  when:
  - fact: Privacy
    is: Closed
- related:
  - verb: has
    entity: membership
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
---

# Only Open and Closed groups show their name and description to people outside them

Anyone can find an Open or Closed group and read its name and description. A group visible to its parent group shows itself to the parent's members, and a Secret group only to people invited or added to it. A deleted group shows itself to nobody.
