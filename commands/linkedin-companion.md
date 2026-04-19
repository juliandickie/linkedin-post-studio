---
description: Generate 5 companion comment prompts on a post theme (for leaving on other creators' posts)
argument-hint: "[theme-or-post-text]"
---

Invoke the `linkedin-post-studio` skill for companion comment prompts.

Input:
- `$ARGUMENTS` — theme, topic, or the text of a parent post you want to comment on (if empty, ask)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/companion-comments.md`.
