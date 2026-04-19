---
title: Companion comments workflow
output_type: companion-comments
last_updated: 2026-04-20
---

# Companion comments workflow

## When this workflow loads

Triggers on:

- "companion comments for X"
- "5 comment prompts on X"
- "comments I can leave on Giants' posts this week"
- `/linkedin-companion`

## Required references (loaded in this order)

1. `references/engagement-tactics.md` — companion comment prompt patterns (§8) and the top-comment-on-Giants tactic
2. `references/post-structure/post-structure-index.md` — for re-frame structural patterns
3. `references/industry/<profile.industry>.md` — conditional; fall back to `references/industry/generic.md` if missing

## Required inputs

- **theme or parent post text** — from request. If absent, ask: "What post or theme are you writing comments for? Paste the post text or describe the topic."
- **profile** — resolved by SKILL.md before this workflow loads

## Generation steps

1. **Identify input type.** The user may provide a specific parent post (pasted text) or a broader theme. If a parent post is given, write comments that fit that exact context. If a theme is given, write comments that work across posts on that theme — valuable without knowing the parent post.

2. **Generate exactly 5 comment prompts**, one per type from `references/engagement-tactics.md` §8:

   - **Opinion** — "Here's how I've seen this play out..." — a perspective grounded in the profile's experience
   - **Re-frame** — "Worth adding: the question isn't just X, it's Y" — shifts the lens without dismissing the original
   - **Data-contribution** — "Quick data point from our own work..." — a specific observation or finding
   - **Question-starter** — "Curious whether anyone here has tested..." — invites dialogue, positions as genuinely curious
   - **Respectful disagreement** — "Agree with 80% of this. One exception..." — acknowledges merit before pushing back

3. **Per-comment constraints:** 25–75 words each. Must stand alone as valuable without knowledge of the parent post. Reflects the profile's voice archetype.

4. **Regulated industry check.** If the profile's industry is in the regulated set (healthcare, legal, finance, real-estate, dental-education), ensure no comment makes specific advice claims requiring a disclaimer. Default to commentary over direct advice.

## Output format

**In chat:** 5 numbered prompts, each labelled with its type:

```
1. [Opinion] <comment text>
2. [Re-frame] <comment text>
3. [Data-contribution] <comment text>
4. [Question-starter] <comment text>
5. [Respectful disagreement] <comment text>
```

**Written to file:** If a parent draft exists in `<data_location>/drafts/`, append the prompts to that draft's `## Companion comment prompts` section. Otherwise create a standalone file: `<data_location>/drafts/YYYY-MM-DD-<slug>-companions.md` using `templates/draft-template.md` with `format: hook-menu` and `status: ready-to-use`.

## Cross-workflow suggestions

- "Want me to write the parent post if you haven't yet?" → `workflows/text-post.md`
- "Want 5 more on a related theme?" → re-dispatch this workflow with a new theme

## Visual companion (v2+)

N/A for comments.
