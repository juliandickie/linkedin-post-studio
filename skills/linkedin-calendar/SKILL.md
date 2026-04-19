---
name: linkedin-calendar
description: Generate a content calendar (week or month) mapped to pillars and format rotation
disable-model-invocation: true
argument-hint: "[week|month] [pillar-mix]"
---

Invoke the `linkedin-post-studio` orchestrator for content calendar generation.

Inputs (positional):
- `$1` — period: `week` | `month` (default `week`)
- `$2` — optional pillar mix override (e.g., `lead-gen`, `thought-leadership`); if omitted, uses profile.operations default or goal-based mix

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/content-calendar.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
