---
domain: discussions
relations:
- entity: thread
  verb: opens
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: app/models/discussion.rb
- kind: code
  role: implementation
  target: app/services/discussion_service.rb
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/starting_a_discussion/index.md
---

# Discussion

A discussion started in a group or directly with chosen people: a title and a context that frames the conversation and the decisions that follow in its thread.

## Information kept

- **Title** — the discussion's title, up to 150 characters
- **Context** — the text at the top of the thread that frames the discussion
