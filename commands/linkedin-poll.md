---
description: Generate a LinkedIn poll (3 options + "Other", 7-day duration)
argument-hint: "[topic]"
---

Invoke the `linkedin-post-studio` skill for poll generation.

Input:
- `$ARGUMENTS` — topic (if empty, ask)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/poll.md`.

Note: max 2–3 polls per month to avoid audience fatigue. If the user's drafts directory has 2+ poll files in the last 30 days, warn before generating.
