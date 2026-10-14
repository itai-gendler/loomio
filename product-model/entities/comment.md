---
relations:
- entity: task
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/models/comment.rb
- kind: code
  role: implementation
  target: app/services/comment_service.rb
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
---

# Comment

A comment in a thread, or a reply to a discussion, poll, vote, outcome or another comment.

## Information kept

- **Body** — what the comment says
- **Reply to** — the item the comment replies to
- **Replies** — how many comments reply to this one
- **Edited at** — when the comment was last edited; every edit is kept and can be compared
- **Thread** — the thread the comment is in

## States

### Visible

The comment shows in the thread.

### Discarded

The comment was discarded; its place in the thread shows Item removed and it can be restored.
