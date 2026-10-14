---
appliesTo:
- type: entity
  id: anonymous-voter
  effect: changes
  to: Voted
permits:
- related:
  - verb: is-listed-as
    entity: user
  when:
  - entity: user
    fact: Deactivated
    is: false
references:
- kind: code
  role: implementation
  target: app/services/anonymous_ballot_service.rb#create
---

# Only the listed person submits their anonymous ballot, once

Submitting marks the person as having voted and stores the ballot apart from them in the same moment.
