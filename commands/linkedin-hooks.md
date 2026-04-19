---
description: Generate 15 hook variations on a topic, mixing categories
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` skill for hook variations.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`; if provided, weights category selection

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/hook-variations.md`.
