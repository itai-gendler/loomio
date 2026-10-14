---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a group, title and context
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product creates the discussion in its own thread, makes the User its thread admin and notifies the people named
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
  contexts:
    web:
      place: api
---

# Start a discussion through the API

## Trigger

An integration acting as a person starts a discussion in a group.

## Outcome

The discussion exists as if the person had started it in the web app.
