---
description: Generate a 60–90 second LinkedIn video script with caption plan
arguments:
  - name: topic
    description: The topic of the video
    required: false
  - name: length
    description: "Target length: 15s | 60s | 90s (default 60s)"
    required: false
---

Invoke the `linkedin-post-studio` skill for video script generation.

Inputs:
- Topic: `{{topic}}` (if empty, ask)
- Length: `{{length}}` (default 60s)

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/video-script.md`.
