---
domain: discussions
references:
- kind: code
  role: implementation
  target: app/models/discussion_template.rb
- kind: code
  role: implementation
  target: app/services/discussion_template_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/discussion_templates_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/templates/index.md
---

# Discussion template

A group's reusable starting point for a discussion: guidance, a default or example title, context, tags, whom to notify by default, suggested poll templates and thread settings. Every new discussion in a group starts from one.

## Information kept

- **Title** — the short name shown in the template list
- **Subtitle** — one line on when to use it
- **Help** — instructions shown at the top of the new discussion form
- **Starts direct discussions** — whether the template starts a direct discussion instead of one in the group
- **Default title** — a title filled in for each new discussion, or an example shown in the empty field
- **Context** — the starting text of the discussion
- **Tags** — tags applied to each new discussion
- **Invite everyone** — whether the whole group is notified by default
- **Suggested poll templates** — polls suggested for the process
- **Thread settings** — whether concurrent polls are allowed and the comment length limit
- **Position** — where the template appears in the group's list

## States

### Visible

It is offered to people starting a discussion.

### Hidden

It is kept but not offered.

### Deleted

It was deleted; discussions started from it are unaffected.
