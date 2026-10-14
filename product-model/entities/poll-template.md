---
domain: polls
references:
- kind: code
  role: implementation
  target: app/models/poll_template.rb
- kind: code
  role: implementation
  target: app/services/poll_template_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/poll_templates_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/poll_templates/index.md
---

# Poll template

A group's own reusable starting point for a vote: a voting method with guidance, example content, options and default settings. Loomio's built-in templates are shipped content that a group can hide; a group's own templates are kept here.

## Information kept

- **Title** — the short name shown in the template list
- **Subtitle** — one sentence on when to use it
- **Help** — guidance shown to someone using the template
- **Poll type** — the voting method polls started from it use
- **Example content** — the example title, details and tags copied into a new poll
- **Options** — the response options copied into a new poll
- **Default settings** — the duration, results visibility, anonymity, vote weights, reason requirement, reminder and quorum a new poll starts with
- **Position** — where the template appears in the group's list

## States

### Visible

People starting a vote can choose it.

### Hidden

It is kept but not offered to people starting a vote.

### Deleted

It was deleted; polls started from it are unaffected.
