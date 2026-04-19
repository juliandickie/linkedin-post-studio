---
description: Generate a 60–90 second LinkedIn video script with caption plan
argument-hint: "[topic] [length]"
---

Invoke the `linkedin-post-studio` skill for video script generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — target length: `15s` | `60s` | `90s` (default 60s)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/video-script.md`.
