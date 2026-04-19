---
name: linkedin-companion
description: Generate 5 companion comment prompts on a post theme (for leaving on other creators' posts)
disable-model-invocation: true
argument-hint: "[theme-or-post-text]"
---

Invoke the `linkedin-post-studio` orchestrator for companion comment prompts.

Input:
- `$ARGUMENTS` — theme, topic, or the text of a parent post you want to comment on (if empty, ask)

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/companion-comments.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
