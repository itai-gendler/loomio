---
appliesTo:
- type: entity
  id: poll
  effect: reads
  facts:
  - Results
permits:
- actors:
  - visitor
  - user
  when:
  - fact: Hide results
    is: 'Off'
- actors:
  - visitor
  - user
  when:
  - fact: Closed at
    present: true
- related:
  - verb: has
    entity: vote
  - verb: casts
    entity: user
  when:
  - fact: Hide results
    is: Until vote
  - entity: vote
    fact: Cast at
    present: true
references:
- kind: code
  role: implementation
  target: app/models/poll.rb#results_visible?
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
---

# People see a poll's results when results are not hidden, after they vote when hidden until vote, and by anyone once it closes

Seeing results also needs being able to read the poll's thread.
