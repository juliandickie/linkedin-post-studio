---
name: linkedin-mine
description: Mine 10–15 post angles from a source (Reddit thread, review file, sales call transcript, URL)
disable-model-invocation: true
argument-hint: "[url-or-file-path-or-text]"
---

Invoke the `linkedin-post-studio` orchestrator for idea mining.

Input:
- `$ARGUMENTS` — URL, file path, or pasted text to extract post angles from

- If `$ARGUMENTS` is a URL → use WebFetch (requires `config.features.online_idea_mining: true`)
- If `$ARGUMENTS` is a file path → read the file
- If `$ARGUMENTS` is pasted text → process directly

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md` (for industry filtering).

Follow the workflow at `../linkedin-post-studio/workflows/idea-mining.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
