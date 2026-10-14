---
entities:
- entity: thread
  shows:
  - Tags
- entity: discussion
  shows:
  - Title
  - Context
- entity: comment
  shows:
  - Body
- entity: poll
  shows:
  - Title
  - Details
  - Options
  - Results
- entity: vote
  shows:
  - Choices
  - Reason
- entity: outcome
  shows:
  - Statement
entryPoints:
- web: /d/{key}
- web: /p/{key}
---

# Thread

A public thread as seen without signing in.
