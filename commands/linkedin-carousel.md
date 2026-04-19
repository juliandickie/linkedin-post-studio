---
description: Generate a LinkedIn carousel brief (6–10 slides)
arguments:
  - name: topic
    description: The topic for the carousel
    required: false
  - name: goal
    description: "Override profile default goal: lead-gen | thought-leadership | brand-awareness | community"
    required: false
  - name: slides
    description: Slide count (default 8; range 6–10)
    required: false
---

Invoke the `linkedin-post-studio` skill for carousel generation.

Inputs:
- Topic: `{{topic}}` (if empty, ask)
- Goal override: `{{goal}}`
- Slide count: `{{slides}}` (default 8)

Resolve the active profile via the standard algorithm.

Dispatch to `skills/linkedin-post-studio/workflows/carousel.md`.
