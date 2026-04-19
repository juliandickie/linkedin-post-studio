---
description: Run the QA checklist and Anti-AI constraint against an existing draft
arguments:
  - name: draft-path-or-text
    description: Path to a draft file OR pasted post text
    required: false
---

Invoke the `linkedin-post-studio` skill for QA review.

Input: `{{draft-path-or-text}}`

- If it looks like a file path → read the file, extract the post text from under "## Post text" if present
- If it looks like pasted text → treat the whole input as the post

Resolve the active profile (for industry-specific compliance checks).

Dispatch to `skills/linkedin-post-studio/workflows/qa-review.md`.

This workflow relies entirely on the always-loaded `anti-ai-constraint.md` and `qa-checklist.md` — no additional references needed.
