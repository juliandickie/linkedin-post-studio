---
name: linkedin-poll
description: Generate a LinkedIn poll (3 options + "Other", 7-day duration)
disable-model-invocation: true
argument-hint: "[topic]"
---

Invoke the `linkedin-post-studio` orchestrator for poll generation.

Input:
- `$ARGUMENTS` — topic (if empty, ask)

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/poll.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).

Note: max 2–3 polls per month to avoid audience fatigue. If the user's drafts directory has 2+ poll files in the last 30 days, warn before generating.
