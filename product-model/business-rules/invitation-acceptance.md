---
appliesTo:
- type: entity
  id: membership
  effect: changes
  to: Active
permits:
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#redeem
---

# Only the invited person accepts an invitation

Whoever follows the single-use link and signs in accepts it; an invitation sent to one address may be accepted with an account using another.
