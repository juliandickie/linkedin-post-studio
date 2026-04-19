---
description: Run the QA checklist and Anti-AI constraint against an existing draft
argument-hint: "[draft-path-or-text]"
---

Invoke the `linkedin-post-studio` skill for QA review.

Input:
- `$ARGUMENTS` — path to a draft file OR pasted post text

- If `$ARGUMENTS` looks like a file path → read the file, extract the post text from under "## Post text" if present
- If `$ARGUMENTS` looks like pasted text → treat the whole input as the post

Resolve the active profile (for industry-specific compliance checks).

Dispatch to `skills/linkedin-post-studio/workflows/qa-review.md`.

This workflow relies entirely on the always-loaded `anti-ai-constraint.md` and `qa-checklist.md` — no additional references needed.
