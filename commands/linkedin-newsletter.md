---
description: Generate a LinkedIn newsletter edition (800–1,200 words) plus a promo post for the feed
argument-hint: "[topic] [goal]"
---

Invoke the `linkedin-post-studio` skill for newsletter generation.

Inputs (positional):
- `$1` — topic (if empty, ask)
- `$2` — optional goal override: `lead-gen` | `thought-leadership` | `brand-awareness` | `community`

Resolve the active profile.

Dispatch to `skills/linkedin-post-studio/workflows/newsletter.md`.

This workflow produces TWO files: the newsletter edition and a linked promo post.
