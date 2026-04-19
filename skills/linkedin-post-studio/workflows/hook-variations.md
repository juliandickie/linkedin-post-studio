---
title: Hook variations workflow
output_type: hook-variations
last_updated: 2026-04-20
---

# Hook variations workflow

## When this workflow loads

Triggers on:

- "hooks for X"
- "generate hooks on X"
- "15 hook variations for X"
- `/linkedin-hooks`

## Required references (loaded in this order)

1. `references/hook-library/hook-index.md`
2. All 12 hook category files from `references/hook-library/hook-*.md` — this workflow loads all of them; each file is small
3. `references/content-pillars.md` — for pillar alignment if the user specifies a goal

## Required inputs

- **topic** — from request. If absent, ask: "What topic do you want hooks for?"
- **goal** (optional) — if provided, used to weight hook category selection toward categories that fit that goal; if not provided, select a variety for stylistic range
- **profile** — resolved by SKILL.md before this workflow loads

## Generation steps

1. **Take input:** topic (required), goal (optional).

2. **Select 5 categories** most likely to produce strong hooks for this topic given the profile's voice archetype. If a goal was specified, apply the category-weighting from `hook-index.md`'s goal-to-category mapping. If no goal, choose a spread across styles so the user has real options.

3. **Generate 3 hook variations per category** — 15 hooks total, specific to the topic.

4. **Per-hook constraints** (from `post-structure-index.md`):
   - ≤140 mobile characters each
   - No emoji
   - No banned vocabulary (per `anti-ai-constraint.md` — enforced by the orchestrator, but write clean first)
   - Include at least one specific element per hook where possible: a number, a proper noun, a named thing, a concrete detail

## Output format

**In chat:** 15 hooks as a numbered list, grouped under 5 category sub-headings. Three hooks per category:

```
### Listicle
1. <hook>
2. <hook>
3. <hook>

### Story
4. <hook>
...
```

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-<slug>-hooks.md` using `templates/draft-template.md`.

Frontmatter fields: `profile`, `format: hook-menu`, `pillar` (if goal was specified; otherwise null), `status: draft`. Body contains the full grouped hook list.

Slug: first 5 words of the topic, lowercase, hyphens.

## Cross-workflow suggestions

- "Pick a hook and I'll draft the full post" → `workflows/text-post.md` with the selected hook passed as input
- "Try 15 more with different categories?" → re-dispatch this workflow
- "Want to build a carousel from your favorite hook?" → `workflows/carousel.md`

## Visual companion (v2+)

N/A.
