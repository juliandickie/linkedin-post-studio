---
description: Analyze a viral LinkedIn post — structure, hook, framework, AI-slop score, ethics — and generate "your version"
arguments:
  - name: post
    description: URL of a LinkedIn post OR pasted post text
    required: false
---

Invoke the `linkedin-post-studio` skill for post teardown.

Input: `{{post}}`

- If URL → use WebFetch to retrieve (if allowed by config); otherwise ask the user to paste the text
- If pasted text → process directly

Resolve the active profile (the "your version" post uses the profile's voice).

Dispatch to `skills/linkedin-post-studio/workflows/post-teardown.md`.
