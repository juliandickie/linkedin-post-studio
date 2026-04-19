---
name: linkedin-qa
description: Run the QA checklist and Anti-AI constraint against an existing draft
disable-model-invocation: true
argument-hint: "[draft-path-or-text]"
---

Invoke the `linkedin-post-studio` orchestrator for QA review.

Input:
- `$ARGUMENTS` — path to a draft file OR pasted post text

- If `$ARGUMENTS` looks like a file path → read the file, extract the post text from under "## Post text" if present
- If `$ARGUMENTS` looks like pasted text → treat the whole input as the post

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md` (for industry-specific compliance checks).

Follow the workflow at `../linkedin-post-studio/workflows/qa-review.md` exactly.

This workflow relies entirely on the always-loaded `../linkedin-post-studio/references/anti-ai-constraint.md` and `../linkedin-post-studio/references/qa-checklist.md` — no additional references needed.
