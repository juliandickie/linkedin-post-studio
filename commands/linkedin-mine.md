---
description: Mine 10–15 post angles from a source (Reddit thread, review file, sales call transcript, URL)
argument-hint: "[url-or-file-path-or-text]"
---

Invoke the `linkedin-post-studio` skill for idea mining.

Input:
- `$ARGUMENTS` — URL, file path, or pasted text to extract post angles from

- If `$ARGUMENTS` is a URL → use WebFetch (requires `config.features.online_idea_mining: true`)
- If `$ARGUMENTS` is a file path → read the file
- If `$ARGUMENTS` is pasted text → process directly

Resolve the active profile (for industry filtering).

Dispatch to `skills/linkedin-post-studio/workflows/idea-mining.md`.
