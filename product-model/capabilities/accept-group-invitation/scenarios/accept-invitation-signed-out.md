---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor follows the invitation link from their email
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::group
- text: The Visitor signs in, or creates an account with the invited address
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::group
- text: The Product accepts the invitation, with every other pending invitation in the same organization, and notifies the inviter
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Invited
    to: Active
    facts:
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
- text: The Product shows the group
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::group
---

# Accept an invitation before signing in

## Trigger

An invitee opens the invitation link from their email without being signed in.

## Outcome

The person is an active member of the group and of every other group in the organization they were invited to, and the inviter is notified.

## Edge cases

- An invitation sent to one address can be accepted with an account using another; the invitation moves to that account.
