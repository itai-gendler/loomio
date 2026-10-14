---
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/thread_markdown_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/topics_controller.rb#markdown
- kind: code
  role: implementation
  target: app/controllers/api/b2/threads_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/ai/index.md
---

# Export thread

Print a thread or save it as Markdown, including Copy for AI, with the same visibility rules as the thread.
