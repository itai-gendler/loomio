---
appliesTo:
- type: entity
  id: reaction
  effect: creates
permits:
- related:
  - verb: adds
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/reaction.rb
---

# People react as themselves to items they can see, in threads that allow reactions

The item's author is notified in Loomio, not by email.
