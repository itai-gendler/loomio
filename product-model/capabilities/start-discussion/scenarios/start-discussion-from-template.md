---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Start discussion and chooses one of the group's templates
  kind: actor
  actor: user
  entities:
  - entity: discussion-template
    effect: reads
    facts:
    - Title
    - Subtitle
  - entity: discussion
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The User edits the title, context, tags and people to notify that the template filled in
  kind: actor
  actor: user
  entities:
  - entity: tag
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product creates the discussion with the template's thread settings, makes the User its thread admin and notifies the people chosen
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
---

# Start a discussion from a template

## Trigger

A member chooses one of the group's discussion templates.

## Outcome

The discussion starts with the template's content, tags and settings, as edited by the member.

## Edge cases

- The whole group is notified by default only when the template says so and the User may notify the whole group.
