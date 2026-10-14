---
kind: alternative
routes:
  web: Web
steps:
- text: The User emails the group's address from their own address or a recognized alias
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: email
- text: Starting threads by email is enabled and the sender is a member of the group
  kind: condition
  actor: user
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Threads from email
  - entity: email-alias
    effect: reads
    facts:
    - Address
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: email
- text: The Product starts a discussion in the group from the email, with the group's default privacy
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: creates
    facts:
    - Title
    - Context
  - entity: thread
    effect: creates
    to: Active
    facts:
    - Private
    - Direct
    - Locked
    - Pinned
    - Tags
    - Reply arrangement
    - Allow comments
    - Allow reactions
    - Concurrent polls
    - Comment length limit
    - Last activity
    with: discussion
  - entity: thread-member
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
    with: thread
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: email
---

# Start a discussion by email

## Trigger

A member emails the group's address, or their own address for the group.

## Outcome

A discussion exists with the email's subject as title, its body as context and its attachments, authored by the member.
