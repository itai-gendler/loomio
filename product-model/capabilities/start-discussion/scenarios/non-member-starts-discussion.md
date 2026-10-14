---
kind: alternative
routes:
  web: Web
steps:
- text: The User writes a title and context for a group they do not belong to
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The group is not secret and lets non-members start discussions
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Privacy
    - Non-members can start discussions
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product creates the discussion in the group, with the User as its thread admin and guest
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

# A non-member starts a discussion

## Trigger

Someone who is not a member of a non-secret group wants to raise a topic with it.

## Outcome

The discussion exists in the group and its author takes part in it as a guest, without access to the group's other private threads.
