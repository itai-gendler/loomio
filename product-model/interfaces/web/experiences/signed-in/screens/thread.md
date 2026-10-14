---
entities:
- entity: thread
  shows:
  - Tags
  - Locked
  - Private
  - Reply arrangement
- entity: discussion
  shows:
  - Title
  - Context
- entity: comment
  shows:
  - Body
  - Reply to
  - Edited at
  collects:
  - Body
- entity: poll
  shows:
  - Title
  - Details
  - Options
  - Results
  - Closing time
  - Closed at
  - Hide results
  - Anonymous
  - Quorum
  collects:
  - Closing time
- entity: vote
  shows:
  - Choices
  - Reason
  - Cast at
  - Weight
  collects:
  - Choices
  - Reason
- entity: anonymous-ballot
  collects:
  - Choices
  - None of the above
- entity: outcome
  shows:
  - Statement
  - Review date
  - Chosen option
  - Event location
  collects:
  - Statement
  - Review date
  - Chosen option
  - Event location
- entity: thread-member
  shows:
  - Guest
  - Thread admin
- entity: user
  shows:
  - Name
  collects:
  - Email
- entity: poll-template
  shows:
  - Title
- entity: tag
  shows:
  - Name
- entity: bookmark
  shows:
  - Item
- entity: group
  shows:
  - Name
- entity: task
  shows:
  - Name
- entity: reaction
  shows:
  - Emoji
entryPoints:
- web: /d/{key}
- web: /p/{key}
---

# Thread

One thread for the people in it: the discussion or poll that opened it, comments, polls with their results, votes and outcomes, the thread's members, and the actions taken there.
