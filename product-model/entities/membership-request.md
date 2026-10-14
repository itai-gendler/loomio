---
domain: members
references:
- kind: code
  role: implementation
  target: app/models/membership_request.rb
- kind: code
  role: implementation
  target: app/services/membership_request_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Membership request

A person's request to join a group that requires approval, with their answer to the group's joining prompt.

## Information kept

- **Introduction** — the requester's answer to the joining prompt, up to 250 characters
- **Decline reason** — the message sent to the requester when the request is declined, up to 500 characters
- **Responded by** — who approved, declined or ignored the request

## States

### Pending

The request waits for review.

### Approved

A reviewer approved it and the requester became a member.

### Declined

A reviewer declined it with a message; the requester may ask again.

### Ignored

A reviewer closed it without telling the requester; it keeps them from asking again.
