---
name: linkedin-repurpose
description: Repurpose long-form content (newsletter, blog, podcast/video transcript) into multiple LinkedIn assets
disable-model-invocation: true
argument-hint: "[source-path-or-url-or-text]"
---

Invoke the `linkedin-post-studio` orchestrator for content repurposing.

Input:
- `$ARGUMENTS` — source content — one of:
  - Pasted newsletter text
  - Blog post URL or file
  - Podcast transcript
  - Video transcript
  - Twitter thread
  - Book chapter

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/repurpose.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).

The workflow will first propose a repurpose plan (N assets mapped to types), then generate the assets you confirm.
