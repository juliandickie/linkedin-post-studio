---
description: Repurpose long-form content (newsletter, blog, podcast/video transcript) into multiple LinkedIn assets
arguments:
  - name: source
    description: Source content — URL, file path, or pasted long-form text
    required: false
---

Invoke the `linkedin-post-studio` skill for content repurposing.

Input: `{{source}}` — one of:
- Pasted newsletter text
- Blog post URL or file
- Podcast transcript
- Video transcript
- Twitter thread
- Book chapter

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/repurpose.md`.

The workflow will first propose a repurpose plan (N assets mapped to types), then generate the assets you confirm.
