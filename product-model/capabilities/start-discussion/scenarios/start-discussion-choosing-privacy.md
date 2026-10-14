---
kind: alternative
routes:
  web: Web
steps:
- text: The User writes a title and context and picks people to notify
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The group allows public or private discussions
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Discussion privacy
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The User chooses whether the discussion is public or private
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product creates the discussion in its own thread with the chosen privacy, makes the User its thread admin and notifies the people chosen
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

# Start a discussion and choose its privacy

## Trigger

A member starts a discussion in a group that allows both public and private threads.

## Outcome

The discussion exists with the privacy the User chose.
