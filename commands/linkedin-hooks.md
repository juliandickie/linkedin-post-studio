---
description: Generate 15 hook variations on a topic, mixing categories
arguments:
  - name: topic
    description: The topic to write hooks for
    required: false
  - name: goal
    description: "Tailor category selection to goal: lead-gen | thought-leadership | brand-awareness | community"
    required: false
---

Invoke the `linkedin-post-studio` skill for hook variations.

Inputs:
- Topic: `{{topic}}` (if empty, ask)
- Goal: `{{goal}}` (optional; if provided, weights category selection)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/hook-variations.md`.
