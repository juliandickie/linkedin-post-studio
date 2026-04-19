---
description: Generate a LinkedIn text post (800–1,000 chars) using the active profile
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` skill for text post generation.

Inputs (positional):
- `$1` — topic (if empty, ask the user)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`

Resolve the active profile via the standard algorithm in `skills/linkedin-post-studio/SKILL.md` (context inference → default → ask if ambiguous).

Dispatch to `skills/linkedin-post-studio/workflows/text-post.md` and follow its instructions exactly.
