---
entities:
- entity: poll
  collects:
  - Title
  - Details
  - Poll type
  - Options
  - Closing time
  - Opening time
  - Anonymous
  - Who can vote
  - Hide results
  - Vote reason
  - Reason length limit
  - Closing soon reminder
  - Notify on open
  - Quorum
  - Vote weights
  - None of the above
  - Ballot limits
- entity: user
  collects:
  - Email
- entity: group
  shows:
  - Name
entryPoints:
- web: /p/new
- web: /p/{key}/edit
---

# Poll form

Starting or editing a proposal or poll from a template: its content, options, timing and settings.
