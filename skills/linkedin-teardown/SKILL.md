---
name: linkedin-teardown
description: Analyze a viral LinkedIn post — structure, hook, framework, AI-slop score, ethics — and generate "your version"
disable-model-invocation: true
argument-hint: "[post-url-or-text]"
---

Invoke the `linkedin-post-studio` orchestrator for post teardown.

Input:
- `$ARGUMENTS` — URL of a LinkedIn post OR pasted post text

- If `$ARGUMENTS` is a URL → use WebFetch to retrieve (if allowed by config); otherwise ask the user to paste the text
- If `$ARGUMENTS` is pasted text → process directly

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md` (the "your version" post uses the profile's voice).

Follow the workflow at `../linkedin-post-studio/workflows/post-teardown.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).
