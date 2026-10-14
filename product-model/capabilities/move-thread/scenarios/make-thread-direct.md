---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to make the thread a direct discussion
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product removes the thread from its group, keeps everyone who took part as its guests and makes it private
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Group
    - Direct
    - Private
  - entity: thread-member
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Make a thread a direct discussion

## Trigger

A thread admin takes a discussion out of its group.

## Outcome

The thread belongs to no group; everyone who took part keeps access, and the User and the thread's author administer it.
