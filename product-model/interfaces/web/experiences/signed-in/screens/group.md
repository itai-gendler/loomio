---
entities:
- entity: group
  shows:
  - Name
  - Description
  - Privacy
  - How people join
  - Joining prompt
  - Parent group
  - Admin count
- entity: membership
  shows:
  - Role
  - Delegate
  - Title
  - Invited by
  - Accepted at
  collects:
  - Title
- entity: membership-request
  shows:
  - Introduction
  collects:
  - Introduction
  - Decline reason
- entity: discussion
  shows:
  - Title
- entity: thread
  shows:
  - Pinned
  - Locked
  - Last activity
- entity: poll
  shows:
  - Title
  - Closing time
- entity: user
  shows:
  - Name
  collects:
  - Email
- entity: discussion-template
  shows:
  - Subtitle
  - Title
- entity: tag
  shows:
  - Name
- entity: email-alias
  shows:
  - Address
entryPoints:
- web: /g/{key}
- web: /{group-handle}/members
---

# Group page

One group: its threads, polls, members, invitations and membership requests, and the actions its members and admins take there.
