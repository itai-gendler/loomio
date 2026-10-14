---
references:
- kind: code
  role: implementation
  target: app/models/group_follow.rb
- kind: code
  role: implementation
  target: app/services/group_follow_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
---

# Group follow

A person following an Open group they have not joined, so its unread activity is included in their catch-up email. Following gives no membership, votes or immediate notifications; joining the group ends it.

## Information kept

- **Followed since** — when the person started following
