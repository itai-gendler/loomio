---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a title and context, chooses tags and picks people or groups to notify
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The group allows only public or only private discussions
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
- text: The Product creates the discussion in its own thread, private or public as the group requires, makes the User its thread admin and notifies the people chosen
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

# Start a discussion in a group

## Trigger

A member wants to raise a topic with the group.

## Outcome

The discussion exists in its own thread with the group's privacy, the User administers it, and the people chosen are notified.

## Edge cases

- A title longer than 150 characters is refused.
- Only people allowed to notify the whole group can choose it as an audience.
