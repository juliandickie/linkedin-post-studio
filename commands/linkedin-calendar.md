---
description: Generate a content calendar (week or month) mapped to pillars and format rotation
arguments:
  - name: period
    description: "week | month (default week)"
    required: false
  - name: pillar-mix
    description: Optional pillar mix override (e.g., "lead-gen" or "thought-leadership")
    required: false
---

Invoke the `linkedin-post-studio` skill for content calendar generation.

Inputs:
- Period: `{{period}}` (default `week`)
- Pillar mix override: `{{pillar-mix}}` (optional; if omitted, uses profile.operations default or goal-based mix)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/content-calendar.md`.
