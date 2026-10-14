---
entities:
- entity: discussion
  collects:
  - Title
  - Context
- entity: thread
  collects:
  - Private
  - Tags
- entity: user
  collects:
  - Email
- entity: tag
  shows:
  - Name
- entity: group
  shows:
  - Name
entryPoints:
- web: /d/new
- web: /d/{key}/edit
---

# Discussion form

Starting or editing a discussion, with the people to notify.
