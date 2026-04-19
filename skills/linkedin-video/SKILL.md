---
name: linkedin-video
description: Generate a 60–90 second LinkedIn video script with caption plan
disable-model-invocation: true
argument-hint: "[topic] [length]"
---

Invoke the `linkedin-post-studio` orchestrator for video script generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — target length: `15s` | `60s` | `90s` (default 60s)

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/video-script.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
