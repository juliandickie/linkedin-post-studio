---
description: Generate a LinkedIn text post (800–1,000 chars) using the active profile
arguments:
  - name: topic
    description: The topic, angle, or specific point for the post
    required: false
  - name: goal
    description: "Override profile default goal: lead-gen | thought-leadership | brand-awareness | community"
    required: false
---

Invoke the `linkedin-post-studio` skill for text post generation.

Inputs:
- Topic: `{{topic}}` (if empty, ask the user)
- Goal override: `{{goal}}`

Resolve the active profile via the standard algorithm in `skills/linkedin-post-studio/SKILL.md` (context inference → default → ask if ambiguous).

Dispatch to `skills/linkedin-post-studio/workflows/text-post.md` and follow its instructions exactly.
