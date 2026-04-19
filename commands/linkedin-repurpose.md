---
description: Repurpose long-form content (newsletter, blog, podcast/video transcript) into multiple LinkedIn assets
argument-hint: "[source-path-or-url-or-text]"
---

Invoke the `linkedin-post-studio` skill for content repurposing.

Input:
- `$ARGUMENTS` — source content — one of:
  - Pasted newsletter text
  - Blog post URL or file
  - Podcast transcript
  - Video transcript
  - Twitter thread
  - Book chapter

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/repurpose.md`.

The workflow will first propose a repurpose plan (N assets mapped to types), then generate the assets you confirm.
