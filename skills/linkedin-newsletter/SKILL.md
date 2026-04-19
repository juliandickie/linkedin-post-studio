---
name: linkedin-newsletter
description: Generate a LinkedIn newsletter edition (800–1,200 words) plus a promo post for the feed
disable-model-invocation: true
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` orchestrator for newsletter generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`

Resolve the active profile via the standard algorithm in `../linkedin-post-studio/SKILL.md`.

Follow the workflow at `../linkedin-post-studio/workflows/newsletter.md` exactly.

Apply universal post-processing per the orchestrator (anti-AI constraint, QA checklist, draft file write, cross-workflow suggestions).

This workflow produces TWO files: the newsletter edition and a linked promo post.
