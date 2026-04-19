---
description: Generate a content calendar (week or month) mapped to pillars and format rotation
argument-hint: "[week|month] [pillar-mix]"
---

Invoke the `linkedin-post-studio` skill for content calendar generation.

Inputs (positional):
- `$1` — period: `week` | `month` (default `week`)
- `$2` — optional pillar mix override (e.g., `lead-gen`, `thought-leadership`); if omitted, uses profile.operations default or goal-based mix

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/content-calendar.md`.
