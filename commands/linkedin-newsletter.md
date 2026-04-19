---
description: Generate a LinkedIn newsletter edition (800–1,200 words) plus a promo post for the feed
arguments:
  - name: topic
    description: The newsletter theme or topic
    required: false
  - name: goal
    description: "Override profile default goal"
    required: false
---

Invoke the `linkedin-post-studio` skill for newsletter generation.

Inputs:
- Topic: `{{topic}}` (if empty, ask)
- Goal override: `{{goal}}`

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/newsletter.md`.

This workflow produces TWO files: the newsletter edition and a linked promo post.
