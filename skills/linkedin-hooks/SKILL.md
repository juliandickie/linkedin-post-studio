---
name: linkedin-hooks
description: Generate 15 hook variations on a topic, mixing categories
disable-model-invocation: true
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` orchestrator for hook variations.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`; if provided, weights category selection

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/hook-variations.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
