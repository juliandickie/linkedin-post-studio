---
name: linkedin-carousel
description: Generate a LinkedIn carousel brief (6–10 slides)
disable-model-invocation: true
argument-hint: "[topic] [goal] [slides]"
---

Invoke the `linkedin-post-studio` orchestrator for carousel generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`
- `$3` — optional slide count (default 8; range 6–10)

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/carousel.md` exactly.

Apply universal post-processing per the orchestrator:
- Anti-AI constraint from `../linkedin-post-studio/references/anti-ai-constraint.md`
- QA checklist from `../linkedin-post-studio/references/qa-checklist.md`
- Output to chat AND write draft to `~/Documents/LinkedIn Post Studio/drafts/`
- Offer cross-workflow suggestions
