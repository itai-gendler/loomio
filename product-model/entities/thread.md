---
relations:
- entity: poll
  verb: holds
  cardinality: one-to-many
- entity: comment
  verb: holds
  cardinality: one-to-many
- entity: thread-member
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: app/models/topic.rb
- kind: code
  role: implementation
  target: app/services/topic_service.rb
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/using_discussions/index.md
---

# Thread

The place one discussion, or one standalone poll, lives with everything said and decided around it: comments, polls, votes and outcomes in order. A thread belongs to a group, or to no group at all as a direct discussion between the people invited to it.

## Information kept

- **Private** — whether only the group's members and the thread's guests may read it; a public thread is readable by anyone
- **Group** — the group the thread is in; none for a direct discussion
- **Direct** — whether the thread belongs to no group
- **Locked** — whether the thread is locked against comments and further changes
- **Pinned** — whether the thread is pinned above the group's other threads
- **Tags** — the group's tags applied to the thread
- **Reply arrangement** — Timeline or Threaded, and whether newest items come first
- **Allow comments** — whether people may comment in the thread
- **Allow reactions** — whether people may react to items in the thread
- **Concurrent polls** — whether more than one poll may be active in the thread at once
- **Comment length limit** — the longest comment the thread accepts, when one is set
- **Last activity** — when something last happened in the thread

## States

### Active

The thread is in use.

### Deleted

The discussion was deleted, taking the thread and its polls with it.
