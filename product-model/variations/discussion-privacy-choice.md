---
kind: configuration
of: capability-scenario
settings:
- entity: group
  fact: Discussion privacy
takesEffect: 'When the discussion is started: the group''s discussion privacy at that moment decides whether the author chooses.'
stability: A started thread keeps its privacy until someone changes it, or until the group's discussion privacy becomes Public only or Private only, which changes every thread in the group.
alternatives:
- id: start-group-discussion
  selectedWhen: Discussion privacy is Public only or Private only; the thread takes that privacy. Groups hidden from the public are always Private only.
- id: start-discussion-choosing-privacy
  selectedWhen: Discussion privacy is Public or private; the author chooses, starting from private.
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#private_default
- kind: code
  role: implementation
  target: app/models/topic.rb#privacy_is_permitted_by_group
- kind: code
  role: implementation
  target: app/models/concerns/group_privacy.rb
---

# Choosing a discussion's privacy

Some groups fix whether their discussions are public or private, while others let each author decide.
