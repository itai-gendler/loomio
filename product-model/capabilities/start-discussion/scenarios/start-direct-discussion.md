---
kind: alternative
routes:
  web: Web
steps:
- text: The User writes a title and context without choosing a group and invites people
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product creates the discussion in a private thread of its own, makes the User its thread admin and adds the invited people as its guests
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
    as: author
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
    with: thread
  - entity: thread-member
    as: invitee
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
    with: thread
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product opens the new thread
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Start a direct discussion

## Trigger

A person wants to discuss something with chosen people outside any group.

## Outcome

A private thread belonging to no group exists; the User and the invited people are its members and the User administers it.
