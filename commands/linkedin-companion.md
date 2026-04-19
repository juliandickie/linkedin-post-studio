---
description: Generate 5 companion comment prompts on a post theme (for leaving on other creators' posts)
arguments:
  - name: theme-or-post
    description: The theme, topic, or the text of a parent post you want to comment on
    required: false
---

Invoke the `linkedin-post-studio` skill for companion comment prompts.

Inputs:
- Theme or parent post text: `{{theme-or-post}}` (if empty, ask)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/companion-comments.md`.
