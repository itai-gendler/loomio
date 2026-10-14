---
kind: primary
routes:
  web: Web
steps:
- text: The User enters email addresses or names and an optional message
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The organization's plan is active and has room for the new members
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Status
    - Member limit
  contexts:
    web:
      place: web::signed-in::group
- text: The Product invites each person and emails each a single-use invitation link in the User's language
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: creates
    to: Invited
    facts:
    - Role
    - Delegate
    - Vote weight
    - Invited by
  contexts:
    web:
      place: web::signed-in::group
---

# Invite people by email

## Trigger

An admin, or a member allowed to add members, wants people to join the group.

## Outcome

Each invitee holds an invitation, receives the invitation email and already counts among the group's members.

## Edge cases

- Up to 100 email addresses are accepted at a time, and invitations per inviter are limited per day.
- People who already belong to the group are left out.
