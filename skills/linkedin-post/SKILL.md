---
name: linkedin-post
description: Generate a LinkedIn text post (800–1,000 chars) using the active profile
disable-model-invocation: true
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` orchestrator for text post generation.

Inputs (positional):
- `$1` — topic (if empty, ask the user)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md` (context inference → default → ask if ambiguous).

Follow the workflow at `../linkedin-post-studio/workflows/text-post.md` exactly.

Apply universal post-processing per the orchestrator:
- Anti-AI constraint from `../linkedin-post-studio/references/anti-ai-constraint.md`
- QA checklist from `../linkedin-post-studio/references/qa-checklist.md`
- Output to chat AND write draft to `~/Documents/LinkedIn Post Studio/drafts/`
- Offer cross-workflow suggestions
