---
description: Generate a LinkedIn carousel brief (6–10 slides)
argument-hint: "[topic] [goal] [slides]"
---

Invoke the `linkedin-post-studio` skill for carousel generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`
- `$3` — optional slide count (default 8; range 6–10)

Resolve the active profile via the standard algorithm.

Dispatch to `skills/linkedin-post-studio/workflows/carousel.md`.
