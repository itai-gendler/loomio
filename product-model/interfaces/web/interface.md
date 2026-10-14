---
type: web
actors:
- visitor
- user
- instance-administrator
entryPoints:
- web: /dashboard
- web: /{group-handle}
references:
- kind: code
  role: implementation
  target: vue/src/routes.js
- kind: code
  role: implementation
  target: config/routes.rb
---

# Loomio web app

The Loomio web application in a browser, also installable as a web app: groups, threads, polls and their settings.
