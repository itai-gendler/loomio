---
type: api
actors:
- user
entryPoints:
- api: /api/b2/
references:
- kind: code
  role: implementation
  target: app/controllers/api/b2/base_controller.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/authenticates_api_key.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/integrations/api/user-api.md
---

# User API

The User API lets other software, including a person's AI agent, act as one Loomio user with that user's API key: reading groups and threads, starting and editing discussions, comments and polls, searching, reporting and syncing a group's members. Every action is limited to what the user may do.
