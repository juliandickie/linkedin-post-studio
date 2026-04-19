---
description: Mine 10–15 post angles from a source (Reddit thread, review file, sales call transcript, URL)
arguments:
  - name: source
    description: URL, file path, or pasted text to extract post angles from
    required: false
---

Invoke the `linkedin-post-studio` skill for idea mining.

Input: `{{source}}`

- If URL → use WebFetch (requires `config.features.online_idea_mining: true`)
- If file path → read the file
- If pasted text → process directly

Resolve the active profile (for industry filtering).

Dispatch to `skills/linkedin-post-studio/workflows/idea-mining.md`.
